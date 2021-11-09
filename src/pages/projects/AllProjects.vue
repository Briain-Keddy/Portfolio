<template>
  <div>
      This the All Project component
      <div v-for="Project in projects"
      :key="Project.id">
        Title: {{ Project.title }}<br>
        Description: {{ Project.description}}<br>
        <router-link :to="{name: project.demo}">Demo</router-link> 
      </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data(){
    return {
      projects: []
    }
  },
  mounted(){
    this.getAllProjects()
  },
  methods: {
    getAllProjects(){
      fetch('./data/projects.json')
      .then(res => res.json())
      .then(data => {
        console.log(data)
        this.projects= data
      })
    }
  }
}
</script>

<style>
</style>