<template>
  <div class="country-list">
    <div class="d-flex justify-content-between">
      <input
        id="search-bar"
        v-model="search"
        type="text"
        placeholder="Search for Country..."
      />
      <select id="selected" v-model="selected" class="mr-4" name="category">
        <option value="">Filter by Regions</option>
        <option value="Asia">Asia</option>
        <option value="Europe">Europe</option>
        <option value="Africa">Africa</option>
        <option value="Europe">Europe</option>
        <option value="Oceania">Oceania</option>
      </select>
    </div>
    <div
      v-for="country in filterCountry"
      :key="country.name"
      class="card col-lg-3"
      style="width: 13rem"
    >
      <router-link
        class="card-block stretched-link text-decoration-none"
        :to="{ path: country.name + '/Details' }"
      >
        <div class="flag-img">
          <img :src="country.flags.png" class="card-img-top" alt="..." />
        </div>

        <div class="card-body">
          <h1 class="py-3">{{ country.name }}</h1>
          <h3 class="d-inline">Population: :</h3>
          <p class="d-inline">{{ country.population }}</p>
          <br />
          <h3 class="d-inline">Region: :</h3>
          <p class="d-inline">{{ country.region }}</p>
          <br />
          <h3 class="d-inline">Capital:</h3>
          <p class="d-inline">{{ country.capital }}</p>
        </div>
      </router-link>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    countriesData: Array,
  },
  data() {
    return {
      search: '',
      selected: '',
    }
  },
  computed: {
    filterCountry() {
      return this.countriesData
        .filter((country) => {
          return country.name.match(this.search)
        })
        .filter((country) => {
          return country.region.match(this.selected)
        })
    },
  },
}
</script>
<style scoped>
#search-bar {
  margin-top: 1%;
  padding: 0.5% 5%;
  margin-left: 7%;
  box-shadow: rgb(100 100 111 / 20%) 0 7px 29px 0;
  border-style: none;
  border-radius: 5px;
  position: relative;
  z-index: 0;
}

#selected {
  margin-top: 1%;
  padding: 0.5% 2%;
  box-shadow: rgb(100 100 111 / 20%) 0 7px 29px 0;
  border-style: none;
  border-radius: 5px;
  background-color: white;
  z-index: 1;
  position: relative;
  right: 7%;
}

.card {
  text-align: left;
  display: inline-block;
  box-shadow: rgb(100 100 111 / 20%) 0 7px 29px 0;
}

.card:hover {
  background-color: lightgray;
}

.flag-img {
  padding-top: 10%;
  height: 115px;
  width: 170px;
}

h1 {
  font-size: 15px;
  color: black;
}

h3 {
  font-size: 12px;
  color: black;
}

p {
  font-size: 12px;
  color: black;
}

.col-lg-3 {
  margin: 5%;
}

.country-list {
  text-align: center;
}
</style>
