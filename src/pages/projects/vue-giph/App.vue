<template>
  <div>
    <b-col>
      <b-row>
        This is the Giphy Viewer
        <GiphyViewer />
      </b-row>
    </b-col>
  </div>
</template>

<script>
import GiphyViewer from '@/pages/projects/vue-giph/GiphyViewer.vue'

export default {
  name: 'App',
  components: {
    GiphyViewer
  }
}
</script>

<style>
</style>