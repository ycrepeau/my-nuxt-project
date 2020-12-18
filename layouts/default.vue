<template lang="pug">
.layout
  header.header
    ul.menu
      li
        NuxtLink(to="/") Home
      li
        NuxtLink(to="/projects") Projects

  .container
    Nuxt

</template>

<script>
export default {
  mounted() {
    console.log('default mounted')
  },
}
</script>

<style lang="scss">
@import '@/assets/scss/app.scss';
.header {
  box-sizing: content-box;
  background-color: $dark-gray;
  padding: 10px;
}
.container {
  margin: 0 auto;
  width: 800px;
}
</style>
