<template>
  <div>
    <div class="search-box">
      <input type="text" v-model="term" v-on:keyup.enter="searchGiphy()" />
      <b-button class="float-right" variant="primary" @click="searchGiphy()">Search</b-button>
    </div>
  
  <b-card-group columns>
    <b-card v-for="gif in gifs" 
      :key="gif.id" 
      :img-src="gif.images.fixed_width.url" 
      :img-alt="git.title"
    >
    <b-card-text>
      <a :href="gif.url" target="_blank">{{ gif.title }}</a>
    </b-card-text>
    </b-card>
  </b-card-group>
  </div>
</template>

<script>
import axios from 'axios';

const GIPHY_URL = "https://api.giphy.com/v1/gifs";
const API_KEY = "MlNSOIaRLVqElstMdH9uDT94U8QKg5kb";

export default {
  name: 'GiphyViewer',
  components: {
  },
  data(){
      return{
        gifs: []
      };
  },
  mouunted(){
    axios.get(`${GIPHY_URL}/trending?api_key=${API_KEY}`)
         .then(respone =>(this.gifs = respone.data.data))
         .catch(error => console.log(error))
  },
  methods:{
    searchGiphy(){
      if(!this.term){
        alert("Please enter a search term");
        return;
      }
      axios.get(`${GIPHY_URL}/search?api_key=${API_KEY}&limit=20`)
         .then(respone =>(this.gifs = respone.data.data))
         .catch(error => console.log(error))
      this.term = "";
    }
  }
}
</script>

<style>
.search-box{
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>