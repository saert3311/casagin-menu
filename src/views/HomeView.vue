<script setup>
import { ref, onMounted, watch } from 'vue'
import CardMenu from '@/components/CardMenu.vue'
import PocketBase from 'pocketbase'

const menu = ref(null)
const img_url = ref(null)
const link = ref('#')
const ID = '469t9tu2733126p'
const pb = new PocketBase('https://api-chefsito.trinum.xyz');

onMounted(async () => {
  menu.value = await pb.collection('restaurants').getOne(ID)
})

watch(menu, async (newValue) => {
  if (newValue) {
    img_url.value = pb.files.getURL(newValue, newValue.image, { thumb: '100x100' })
    link.value = menu.value.link || '#'
  }
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
      <CardMenu />
    </div>
  </div>
</template>
