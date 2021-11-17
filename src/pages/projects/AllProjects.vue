<template>
  <div>
    <input type="text" v-model="searchTerm" /><br><br>
    <button @click="searchProjects">Search</button><br>
    <div>
      <b-card 
        header="project"
        header-text-varient="white"
        header-bg-varient="dark"
        v-for="project in projects"
        :key="project.id">
          Title: {{ project.title }}<br>
          Description: {{ project.description}}<br>
          <router-link :to="{name: project.demo}">Demo</router-link>
      </b-card>
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
      projects: [],
      searchTerm: ""
    }
  },

  computed:{
    filterProjects(){
      return this.projects.filter(project => {
        return project.title.toLowerCase().includes(this.searchTerm.toLowerCase())
      })
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
    },

    searchProjects(){}
  }
}
</script>

<style>
</style>