<template>
  <div class="addBooking">
    <button @click="increment">Count is: {{state.count}}, double is: {{state.double}}</button>
  </div>
</template>

<script>
import { reactive, computed } from "vue";
//import states from "../assets/bookinglist.json";

export default {
  name: "AddBooking",

  setup() {

    return {
      state,
      increment
    };
  }
};
</script>