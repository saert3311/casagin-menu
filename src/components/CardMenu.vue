<script setup>
import { Button } from '@/components/ui/button'
import {
  Card,
  CardContent,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'
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
            <Button variant="outline" class="w-full">
              Login with Apple
            </Button>
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
