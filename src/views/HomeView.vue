<script setup>
import MenuDisplay from '@/components/MenuDisplay.vue';
import MenuLoader from '@/components/MenuLoader.vue';
</script>
<template>
  <Suspense>
    <MenuDisplay />
    <template #fallback>
      <MenuLoader />
    </template>
  </Suspense>
</template>
