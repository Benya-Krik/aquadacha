<template>
  <header-components />
  <index-components />
  <footer-components />
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import IndexComponent from './components/page/IndexComponent.vue'
import FooterComponent from './components/FooterComponent.vue'
export default {
  name: 'App',
  components: {
    'header-components': HeaderComponent,
    'index-components': IndexComponent,
    'footer-components': FooterComponent
  }
}
</script>

<style lang="scss">
</style>
