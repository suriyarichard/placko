<template>
  <v-app>
    <v-main>
      <HelloWorld />
      <!-- <Suriya /> -->
      <Map />
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Map from "./components/map1";
// import suriya from "./components/suriya";

export default {
  name: "App",

  components: {
    HelloWorld,
    Map,
    // suriya,
  },

  data: () => ({
    //
  }),
};
</script>
