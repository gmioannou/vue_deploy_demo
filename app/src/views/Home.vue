<template>
  <div class="home">
    <h2>Deploy with docker and nginx!</h2>
    <h3>This is a demo app!</h3>
    <h3>Api: {{ apiUrl }}</h3>
    <h3>Geoserver: {{ geoserverUrl }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      apiUrl: '',
      geoserverUrl: ''
    }
  },
  mounted() {
    this.apiUrl = process.env.VUE_APP_API_URL
    this.geoserverUrl = process.env.VUE_APP_GEOSERVER_URL
  }

}
</script>
