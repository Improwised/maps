<template>
  <div style="box-shadow: 0 0 5px rgb(0 0 0 / 30%)">
    <div class="container c1">
      <h3><b>Where in the world?</b></h3>
      <button class="toggle"><fa icon="moon" />Dark Mode</button>
    </div>
    <!-- <div class="container c1">
      <div class="form-c1">
        <i><fa class="search-icon" icon="magnifying-glass" /></i>
        <input v-model="search" type="text" placeholder="Search For Country..." />
      </div>
      <div class="drop1">
        
        <div class="drop2">
          <select style="border:0; background-color:white">
          <option>Filter By Region</option>
          <option v-for="country in countryInfo" :key="country">{{country.region}}</option>
          </select>
          <p>Filter By Region</p>
          <button><fa icon="chevron-down" /></button>
        
        <div class="drop3">
          <p>Africa</p>
          <p>America</p>
          <p>Asia</p>
          <p>Europe</p>
          <p>Oceania</p>
        </div>  -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      countryInfo: [],
      url: 'https://restcountries.com/v2/all',
      search: ' ',
    }
  },
  computed: {
    searchCountry() {
      return this.countryInfo.filter((country) => {
        return country.name.match(this.search)
      })
    },
  },
  async created() {
    const res = await this.$axios.$get(this.url)
    this.countryInfo = res
  },
}
</script>
