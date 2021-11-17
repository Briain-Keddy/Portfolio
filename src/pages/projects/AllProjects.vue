<template>
  <div class="columns">
    <div class="column">
      <b-field label=""></b-field>
      <div class="card"
        v-for="project in filterProjects"
        :key="project.id">
      >
        <div class="card-image">
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <figure class="image is-48x48">
                <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
              </figure>
            </div>
            <div class="media-content">
              <p class="title is-4">{{ project.title }}</p>
              <p class="subtitle is-6">
                <b-taglist>
                  <b-tag v-for="tag in project.tag" :key="tag" type="is-primary"></b-tag>
                </b-taglist>
              </p>
              <b-field v-for="tag in project.tags" :key="tag">
                <b-tag>{{ tag }}</b-tag>
              </b-field>
            </div>
          </div>
          <div class="content">
            {{ project.description }}
          </div>
        </div>
      </div>
    </div>
    <input type="text" v-model="searchTerm" />
    <div>
      <b-card 
        header="project"
        header-text-varient="white"
        header-bg-varient="dark"
        v-for="project in filterProjects"
        :key="project.id">
          Title: {{ project.title }}<br>
          Description: {{ project.description}}<br>
          <router-link v-if="project.demo" :to="{name: project.demo}">Demo</router-link>
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
  }
}
</script>

<style>
</style>