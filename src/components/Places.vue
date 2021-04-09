<template>
  <div>
    <h1>Places</h1>
    <div class="show_Places_panel">
      <button v-on:click="isHidden = false">Get Places</button>
      <div class="show_Places" v-if="!isHidden">
        <SearchPlaces/>
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
  computed: {
    placesList() {
      return states;
    },
  },
  methods: {
    showPlaces() {},
  },
  data() {
    return {
      isHidden: true,
    };
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
  background-color: #1aa832;
  color: white;
  border: 1px solid #ccc;
}
</style>