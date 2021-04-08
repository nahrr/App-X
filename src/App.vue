<template>
  <div id="app">
    <!-- <Count /> -->
    <AddBooking />
  </div>
</template>

<script>
//import Count from "@/components/Count";
import AddBooking from "./components/AddBooking.vue";
export default {
  name: "app",
  components: { AddBooking },
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
