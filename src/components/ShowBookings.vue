<template>
  <div>
    <h1>Bookings</h1>
    <div class="show_Bookings_panel">
      <FilterBookings/>
      <button v-on:click="isHidden = false">Get Bookings</button>
      <div class="show_Bookings" v-if="!isHidden">
        <SearchBookings/>
        <div
          v-for="bookingData in bookingList"
          :key="bookingData.id"
          class="booking_data"
        >
          <div class="bookings">
            <div>
              {{ bookingData.country }}
            </div>
            <div>
              {{ bookingData.location }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBookings from "./SearchBookings.vue";
import FilterBookings from "./FilterBookings.vue";
import states from "../assets/bookinglist.json";
export default {
  name: "ShowBookings",
  components: { SearchBookings, FilterBookings },
  computed: {
    bookingList() {
      return states;
    },
  },
  methods: {
    showBookings() {},
  },
  data() {
    return {
      isHidden: true,
    };
  },
};
</script>

<style scoped>
.booking_data {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
}

.bookings {
  flex-grow: 8;
  text-align: left;
  padding-left: 1rem;
  display: flex;
  justify-content: space-between;
}
button {
  padding: 1rem;
  background-color: #1aa832;
  color: white;
  border: 1px solid #ccc;
}
</style>