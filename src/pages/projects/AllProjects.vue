<template>
  <div class="columns">
    <div class="column">
      <b-field label="Search Projects">
        <b-input v-model="searchTerm"></b-input>
      </b-field>
      <div class="card"
        v-for="project in filterProjects"
        :key="project.id">
        <div class="card-image">
          <figure class="image is-4by3">
            <img v-if="project.images[0]" :src="`./images/${project.images[0]}`">
            <img v-else src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
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
                  <b-tag 
                    v-for="tag in project.tags" 
                    :key="tag" 
                    type="is-primary"
                  >
                    {{ tag }}
                  </b-tag>
                </b-taglist>
              </p>
              <p v-if="project.demo.length > 0" class=" is-4">
                <router-link :to="{name: project.demo}" target="_blank">Demo</router-link>
              </p>
              <p v-if="project.website">
                <a :href="project.website" target="_blank">Website</a>
              </p>
              <p v-if="project.links.github">
                <a :href="project.links.github" target="_blank">Github</a>
              </p>
            </div>
          </div>
          <div class="content">
            {{ project.description }}
          </div>
        </div>
      </div>
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