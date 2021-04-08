<template>
  <div>
    <h1>Bokningar</h1>
  <div class="add_Booking">
    <button v-on:click="getBookingsData">Get Bookings</button>
    <div v-for="bookingData in bookingList" :key="bookingData.id" class="booking-data">
      <div class="bookings">
        <span>{{ bookingData.location }} </span>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "AddBooking",
  data() {
    return {
      bookingList: [],
    };
  },
  methods: {
    getBookingsData() {
      fetch("bookinglist.json")
        .then((response) => response.json())
        .then((data) => (this.bookingList = data));
    },
  },
};
</script>

<style scoped>
.booking-data{
    display: flex;
  align-items: center;
  margin-top: 20px;
  margin-left: 20px;
  border-bottom: 2px solid #ccc;
  padding: 20px;
}

.bookings {
  flex-grow: 8;
  text-align: left;
  padding-left: 20px;
}
button {
  padding: 10px;
  background-color: #1aa832;
  color: white;
  border: 1px solid #ccc;
}
</style>