<template>
  <div>
    <h1>Places</h1>
    <SearchPlaces/>
    <div class="show_Places_panel">
      <button v-on:click="isHidden = false">Get Places</button>
      <div class="show_Places" v-if="!isHidden">
        <div class="search_panel">
          <label>Search places:</label>
          <input type="text" v-model="searchValue" placeholder="Filter..." />
        </div>
        <div
          v-for="placesData in placesList"
          :key="placesData.location"
          class="place_data"
        >
          <div class="places">
            <div>
              {{ placesData.country }}
            </div>
            <div>
              {{ placesData.location }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchPlaces from "./SearchPlaces.vue";
import states from "../assets/places.json";
export default {
  name: "Places",
  components: { SearchPlaces },
  data() {
    return {
      isHidden: true,
      searchValue: "",
    };
  },
  computed: {
    placesList() {
      var tempPlaces = states;

      if (this.searchValue != "" && this.searchValue) {
        tempPlaces = tempPlaces.filter((item) => {
          return item.location
            .toUpperCase()
            .includes(this.searchValue.toUpperCase());
        });
      }
      return tempPlaces;
    },
  },
};
</script>

<style scoped>
.place_data {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
}

.places {
  flex-grow: 8;
  text-align: left;
  padding-left: 1rem;
  display: flex;
  justify-content: space-between;
}
button {
  padding: 1rem;
  background-color: #4CAF50;
  color: white;
  border: 1px solid #ccc;
  cursor: pointer;
  transition: all 0.2s;
}
button:hover{
  background-color: #3ff15c;  /* Green */
  color: white;
}
.search_panel {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
}
label{
  font-weight: bold;
  margin-right: 1rem;
}
input:focus {
  background-color: rgb(204, 248, 175);
}
input:hover{
    background-color: rgb(204, 248, 175);
}
</style>