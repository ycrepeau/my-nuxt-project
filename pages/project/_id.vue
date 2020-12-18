<template lang="pug">
  
  div(v-if="$apollo.loading")
    | Loading data from strapi server...
  div(v-else)
    p {{projects[0].title}}
    p(v-for="category in projects[0].categories" :key="category.id")
      | {{category.title}}
    p {{projects[0].description}}
  
</template>

<script>
import projectQuery from '~/apollo/queries/projects/project.gql'
import { getStrapiMedia } from '~/utils/medias'

export default {
  async asyncData({ params }) {
    const { id } = params // When calling /abc the slug will be "abc"
    return { id }
  },

  data() {
    return {
      projects: [],
      query: '',
    }
  },
  apollo: {
    projects: {
      query: projectQuery,
      variables() {
        return { id: this.$route.params.id }
      },
    },
  },
  methods: {
    getStrapiMedia,
  },

  mounted() {
    console.log('project.vue mounted')
    console.log(projectQuery)
  },
}
</script>
