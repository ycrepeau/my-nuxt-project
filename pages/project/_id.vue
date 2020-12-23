<template lang="pug">
  
  div(v-if="waitData")
    | Loading data from strapi server...
  div(v-else)
    p {{projects[0].title}}
    p(v-for="category in projects[0].categories" :key="category.id")
      | {{category.title}}
    p {{projects[0].description}}
    div(v-for="content in projects[0].content")
      p Content-type: {{content.__typename}}
  
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
  computed: {
    waitData() {
      return this.$apollo.loading || this.projects.length === 0
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
