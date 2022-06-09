<template>
  <div id="app">
    <BaseHeader></BaseHeader>
  </div>
</template>

<script>
import BaseHeader from './components/header/BaseHeader.vue';

export default {
  name: 'App',
  components: {
    BaseHeader
  }
}
</script>

<style lang="scss">
@import './assets/style/global.scss';

#app {}
</style>
