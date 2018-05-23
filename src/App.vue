<template>
  <div id="app">
      <nav-bar logo="Social" url="#" cor ="green darken-1" />
    <router-view/>
  </div>
</template>

<script>

import NavBar from '@/components/layouts/NavBar'

export default {
  name: 'App',
  components:{
    NavBar
  }
}
</script>

<style>

</style>
