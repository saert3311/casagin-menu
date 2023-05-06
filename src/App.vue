<script>
import MenuHeader from './components/MenuHeader.vue'
import ButtonsWrapper from './components/ButtonsWrapper.vue'
export default {
  components: {
    MenuHeader,
    ButtonsWrapper,
  }
}
</script>

<template>
  <div class="container">
    <div class="columns is-centered is-flex-direction-column">
      <MenuHeader />
      <ButtonsWrapper />
    </div>
  </div>
</template>

<style>
body {
  background-color: #343436;
}
</style>
