<template>
  <div>
    <app-header/>
      <div>
        <app-featured/>
        <app-menu/>
        <app-call-us/>
        <app-newsletter/>
      </div>
    <app-footer/>
  </div>
</template>

<script>
  import appHeader from'./components/Header-footer/Header.vue';
  import appFooter from'./components/Header-footer/Footer.vue';
  import appFeatured from './components/Featured/index.vue';
  import appMenu from './components/Menu/index.vue';
  import appCallUs from './components/CallUs/index.vue';
  import appNewsletter from './components/Newsletter/index.vue';

  export default {
    components: {
      appHeader,
      appFooter,
      appFeatured,
      appMenu,
      appCallUs,
      appNewsletter
    }
  }
</script>

<style>
  @import './assets/style.css';
</style>
