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
              v-on:click="sizeOfList = 'showAll'"
              class="search--panel--btn"
            >
              Show 1000
            </button>
            <button
              v-on:click="sizeOfList = 'showHalf'"
              class="search--panel--btn"
            >
              Show 500
            </button>
            <button
              v-on:click="sizeOfList = 'showTenth'"
              class="search--panel--btn"
            >
              Show 100
            </button>
            <button
              v-on:click="sizeOfList = 'showHundredth'"
              class="search--panel--btn"
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
    placesSize() {
      let size = 10000;
      switch (this.sizeOfList) {
        case "showHundredth":
          size = 10;
          break;
        case "showTenth":
          size = 100;
          break;
        case "showHalf":
          size = 500;
      }
      return states.slice(0, size);
    },
    // condition ? exprIfTrue : exprIfFalse
    placesList() {
      return !this.searchValue
        ? this.placesSize
        : this.placesSize.filter((item) => {
            const value = this.searchValue.toUpperCase();
            return (
              item.location.toUpperCase().includes(value) ||
              item.country.toUpperCase().startsWith(value)
            );
          });
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
  margin: 0;
  max-height: 1rem;
  display: flex;
  align-items: center;
}

.search--panel--btn__container {
  display: flex;
  flex: 1;
  justify-content: flex-end;
  column-gap: 8px;
}
</style>