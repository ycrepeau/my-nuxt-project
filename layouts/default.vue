<template lang="pug">
.layout
  header.header.
    The header will be located here
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
  color: $primary-color;
  background-color: $secondary-color;
  height: 24px;
  padding: 10px;
}
.container {
  margin: 0 auto;
  width: 800px;
}
</style>
