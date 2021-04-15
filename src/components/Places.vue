<template>
  <div>
    <h1>Places</h1>
    <div class="show_places_panel">
      <button v-on:click="isHidden = false" v-if="isHidden">Get Places</button>
      <div class="show_places" v-if="!isHidden">
        <div class="search_panel">
          <label>
            Search places:
            <input type="text" v-model="searchValue" placeholder="Filter..." />
          </label>
          <div class="search--panel--btn__container">
            <button
              class="search--panel--btn"
              v-on:click="sizeOfList = 'showAll'"
            >
              Show 1000
            </button>
            <button
              class="search--panel--btn"
              v-on:click="sizeOfList = 'showHalf'"
            >
              Show 500
            </button>
            <button
              class="search--panel--btn"
              v-on:click="sizeOfList = 'showTenth'"
            >
              Show 100
            </button>
            <button
              class="search--panel--btn"
              v-on:click="sizeOfList = 'hundredth'"
            >
              Show 10
            </button>
          </div>
        </div>
        <div
          v-for="placesData in placesList"
          :key="placesData.id"
          class="place_data"
        >
          <div class="places">
            <div>
              {{ placesData.country }}
            </div>
            <div>
              {{ placesData.location }}
            </div>
            <div>
              {{ placesData.id }}
            </div>
            <div class="card">
              <img v-bind:src="placesData.image" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import states from "../assets/places.json";

export default {
  name: "Places",
  components: {},
  data() {
    return {
      isHidden: true,
      searchValue: "",
      sizeOfList: "",
    };
  },
  computed: {
    placesList() {
      var tempPlaces = states;
      console.log(this.sizeOfList);

      if (this.sizeOfList === "hundredth") {
        tempPlaces = states.slice(0, 10);
      } else if (this.sizeOfList === "showTenth") {
        tempPlaces = states.slice(0, 100);
      } else if (this.sizeOfList === "showHalf") {
        tempPlaces = states.slice(0, 500);
      } else {
        tempPlaces = states.slice(0, 1000);
      }
      //Not rly sure about this to be honest
      if (this.searchValue != "" && this.searchValue) {
        tempPlaces = tempPlaces.filter((item) => {
          return (
            item.location
              .toUpperCase()
              .includes(this.searchValue.toUpperCase()) ||
            item.country
              .toUpperCase()
              .startsWith(this.searchValue.toUpperCase())
          );
        });
      }
      return tempPlaces;
    },
  },
};
</script>

<style scoped>
button {
  padding: 1rem;
  background-color: #dddddd;
  color: rgb(218, 218, 218);
  border: 1px solid #ccc;
  cursor: pointer;
  transition: all 0.2s;
  color: #2c3e50;
}

button:hover {
  background-color: rgb(204, 248, 175);
}

img {
  width: 10rem;
  height: 5rem;
  object-fit: cover;
  border-radius: 0.1rem;
  box-shadow: 1px 1px 3px 1px rgba(0, 0, 0, 0.5);
}

input:hover {
  background-color: rgb(204, 248, 175);
}

input:focus {
  background-color: rgb(204, 248, 175);
}

label {
  font-weight: bold;
  margin-right: 1rem;
}
.place_data:nth-child(odd) {
  background-color: rgb(245, 239, 239);
}

.places {
  flex-grow: 8;
  text-align: left;
  padding-left: 1rem;
  display: flex;
  justify-content: space-between;
  font-weight: bold;
}

.place_data {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
}

.search_panel {
  display: flex;
  align-items: center;
  margin-top: 1rem;
  margin: 0 auto;
  border-bottom: 2px solid #ccc;
  padding: 1rem;
  max-width: 55rem;
  justify-content: space-between;
}
.search--panel--btn {
  margin-left: 0.5rem;
}
</style>