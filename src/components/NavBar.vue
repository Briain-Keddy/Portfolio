<template>
  <div>
      <router-link :to="{name: 'home'}">Home</router-link> |
      <router-link :to="{name: 'about'}">About</router-link> |
      <router-link :to="{name: 'projects'}">My Projects</router-link> |
      <router-link :to="{name: 'contact'}">Contact</router-link> 
  </div>
</template>

<script>

export default {
  name: 'NavBar'
}
</script>

<style>
</style>