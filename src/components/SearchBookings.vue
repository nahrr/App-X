<template>
  <div id="app">
    <div class="search-wrapper">
    <label>Search title:</label>
    <input type="text" v-model="search" placeholder="Search Bookings.." />
      
    </div>
    <div class="wrapper">
      <!-- <div class="card" v-for="booking in filteredList"> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBookings",
  props: {
    booking: {
      type: Object,
      required: true,
    },
  },

  //   computed: {
  //     filteredList() {
  //       return this.postList.filter(post => {
  //         return post.location.toLowerCase().includes(this.search.toLowerCase())
  //       })
  //     }
  //   }
};
</script>

<style scoped>

</style>
