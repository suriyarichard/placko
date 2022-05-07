<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Map />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Map from '../components/Map.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    Map
  }
}
</script>
