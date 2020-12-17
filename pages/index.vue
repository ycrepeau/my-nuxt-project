<template lang="pug">
  #home
    H1 {{home.title}}

    p {{home.bio}}

  
</template>

<script>
import homeQuery from '~/apollo/queries/home/home.gql'

export default {
  data() {
    return {
      home: {},
      query: '',
    }
  },
  apollo: {
    home: {
      prefetch: true,
      query: homeQuery,
    },
  },

  mounted() {
    console.log('index.vue mounted')
    console.log(homeQuery)
  },
}
</script>

<style scoped lang="scss">
@import '@/assets/scss/app.scss';
</style>
