<template>
  <div id="app">
   
    <Places />
  </div>
</template>

<script>
//import Count from "@/components/Count";
import Places from "./components/Places.vue";
export default {
  name: "app",
  components: { Places },
};
</script>
<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
