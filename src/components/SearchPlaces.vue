<template>
  <div>
    <div class="search_panel">
    <label>Search places:</label>
    <input type="text" v-model="search" placeholder="Filter..." />
      
    </div>
    <div class="wrapper">
      <!-- <div class="card" 
      v-for="filterBooking in filteredList"
      :key="filterBooking.id"
       >
        <div class="bookings">
            <div>
              {{ bookingData.country }}
            </div>
       
     </div> -->
    <!-- </div> -->
    </div>
  </div>
</template>

<script>
//import states from "../assets/places.json";
export default {
  name: "Places",
  props: {
    booking: {
      type: Object,
      required: true,
    },
  },
  methods: {
    bar: function () {
      this.$root.$refs.Places.showPlaces();
    },
  },

  computed: {
    filteredList() {
      return this.bar.filter((post) => {
        return post.location.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
.search_panel {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
}
</style>
