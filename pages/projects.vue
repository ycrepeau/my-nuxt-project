<template lang="pug">
  div
    H1 Projects
    .grid-y.grid-margin-y
      .cell(v-for="project in projects" :key="project.id")
        .grid-x.grid-margin-x
          .cell.medium-6
            NuxtLink(':to'="'/project/' + project.id")
              img(':src'="getStrapiMedia(project.coverImage.url)"
                ':alt'='project.title')
          .cell.medium-6
            NuxtLink(':to'="'/project/' + project.id")
              H3 {{project.title}}
              span.secondary.badge(v-for="(category) in project.categories" ':key'="category.id").
                {{category.title}}
            p.
              {{project.description}}
              
            NuxtLink(':to'="'/project/' + project.id")
              p View project 👉


</template>

<script>
import projectsQuery from '~/apollo/queries/projects/projects.gql'
import { getStrapiMedia } from '~/utils/medias'

export default {
  data() {
    return {
      projects: [],
      query: '',
    }
  },
  apollo: {
    projects: {
      prefetch: true,
      query: projectsQuery,
    },
  },
  methods: {
    getStrapiMedia,
  },

  mounted() {
    console.log('project.vue mounted')
    console.log(projectsQuery)
  },
}
</script>

<style scoped lang="scss">
.badge {
  padding: 5px 10px;
  margin: 0 5px;
  margin-bottom: 15px;
}

h3 {
  margin-bottom: 0px;
}
</style>
