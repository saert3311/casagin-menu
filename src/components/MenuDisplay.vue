<script setup>
import { computed } from 'vue'
import CardMenu from '@/components/CardMenu.vue'
import PocketBase from 'pocketbase'

const ID = '469t9tu2733126p'
const pb = new PocketBase('https://api-chefsito.trinum.xyz')

// Make the setup function async by awaiting the data fetch
const menu = await pb.collection('restaurants').getOne(ID, {
  expand: 'menus_via_restaurant',
})

// Compute derived values reactively
const img_url = computed(() => {
  return menu ? pb.files.getURL(menu, menu.image, { thumb: '100x100' }) : null
})

const link = computed(() => {
  return menu?.link || '#'
})

const links_menus = computed(() => {
  if (!menu?.expand?.menus_via_restaurant) return []

  return menu.expand.menus_via_restaurant.map(menuItem => ({
    nombre: menuItem.nombre,
    id: menuItem.id,
    file: pb.files.getURL(menuItem, menuItem.archivo),
  }))
})
</script>

<template>
  <div class="flex min-h-svh flex-col items-center justify-center gap-6 bg-muted p-6 md:p-10">
    <div class="flex w-full max-w-sm flex-col gap-6">
      <a :href="link" class="flex items-center gap-2 self-center font-bold text-lg" target="_blank"
        rel="noopener noreferrer">
        <div class="flex items-center justify-center rounded-md bg-primary text-primary-foreground">
          <img :src="img_url" alt="Logo" class="size-30 rounded object-cover" v-show="img_url" />
        </div>
      </a>
      <CardMenu :menu_list="links_menus" v-if="menu" />
    </div>
  </div>
</template>
