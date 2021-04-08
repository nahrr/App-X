<template>
  <div>
    <h1>Bokningar</h1>
    <div class="add_Booking">
      <button v-on:click="showBookings">Get Bookings</button>
      <div
        v-for="bookingData in bookingList"
        :key="bookingData.id"
        class="booking-data"
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
</template>

<script>
import states from "../assets/bookinglist.json";
export default {
  name: "AddBooking",
  computed: {
    bookingList() {
      return states;
    },
  },
  methods:{
    showBookings(){
 
    }
  }
};

</script>

<style scoped>
.booking-data {
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