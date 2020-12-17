<template lang="pug">
  div
    H1 Projects
    .cell(v-for="project in projects" :key="project.id")
      .grid-x.grid-margin-x
        .cell.medium-6
          a(':to'="'project/' + project.slug")
            img(':src'="getStrapiMedia(project.coverImage.url)"
              ':alt'='project.title')
        .cell.medium-6
          a(':to'="'project/' + project.slug")
            H3 {{project.title}}
            span.secondary.badge(v-for="(category) in project.categories" ':key'="category.id").
              {{category.title}}
          p.
            {{project.description}}
            
          a(':to'="'project/' + project.slug")
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
