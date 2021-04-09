<template>
  <div id="app">
   
    <ShowBookings />
  </div>
</template>

<script>
//import Count from "@/components/Count";
import ShowBookings from "./components/ShowBookings.vue";
export default {
  name: "app",
  components: { ShowBookings },
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
