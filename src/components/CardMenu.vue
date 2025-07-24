<script setup>
import { Button } from '@/components/ui/button'
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'

const props = defineProps([
  'menu_list',
])
</script>
<template>
  <div class="flex flex-col gap-6">
    <Card>
      <CardHeader class="text-center">
        <CardTitle class="text-xl">
          Menus Disponibles
        </CardTitle>
      </CardHeader>
      <CardContent>
        <div class="grid gap-6">
          <div class="flex flex-col gap-4">
            <a v-for="(menu, index) in menu_list" :key="index" :href="menu.file" target="_blank"
              rel="noopener noreferrer">
              <Button variant="outline" class="w-full">
                {{ menu.nombre }}
              </Button>
            </a>
          </div>
        </div>
      </CardContent>
    </Card>
    <div
      class="text-balance text-center text-xs text-muted-foreground [&_a]:underline [&_a]:underline-offset-4 [&_a]:hover:text-primary">
      Un pequeño menu desarrollado por <a href="https://trinum.xyz" target="_blank" ref="noreferer">Jose Duarte</a>.
    </div>
  </div>
</template>
