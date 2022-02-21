<template>
  <div class="nav-item">
    <div class="pl-4 pr-3 pr-5 d-flex pt-5 justify-content-between">
      <input
        class="search w-25 mx-4 mt-5 p-3 w-25"
        placeholder="Search for a country..."
        type="text"
      />
      <select
        id=""
        class="options w-25 mx-4 mt-5 p-2 w-25 border-0 bg-white shadow w-30 font-font-weight-normal"
      >
        <option value="volvo">Filter By Region</option>
        <option value="Europe">Europe</option>
        <option value="Africa">Africa</option>
        <option value="Europe">Europe</option>
        <option value="Oceania">Oceania</option>
      </select>
    </div>
    <div class="row">
      <div
        v-for="(country, index) in countries"
        :key="index"
        class="col-lg-3 h-auto w-auto p-5 pl-5"
        style="width: 16rem"
      >
        <router-link
          class="card m-4 h-100"
          :to="{ path: 'vatsal/' + country.name + '/countrydetails' }"
        >
          <div class="flag-img">
            <img
              class="card-img-top p-4 pt-5 w"
              :src="country.flags.png"
              alt="..."
            />
          </div>
          <div class="card-body">
            <h5 class="card-title">{{ country.name }}</h5>
            <p class="card-text">
              Population:
              {{ country.population }} <br />

              Region:
              {{ country.region }} <br />

              Capital:
              {{ country.capital }} <br />
            </p>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    countries: Array,
  },
  data() {
    return {
      search: '',
      selected: '',
    }
  },
}
</script>
<style scoped>
.search {
  border-radius: 0.7em;
  width: 30em;
  border: none;
  box-shadow: rgb(100 100 111 / 20%) 0 7px 20px 0;
}
</style>
