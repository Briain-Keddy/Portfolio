<template>
  <div>
    <b-col>
      <b-row>
        this is the app
        <GiphyViewer />
      </b-row>
    </b-col>
  </div>
</template>

<script>
import GiphyViewer from '@/pages/projects/GiphyViewer.vue'

export default {
  name: 'App',
  components: {
    GiphyViewer
  }
}
</script>

<style>
</style>