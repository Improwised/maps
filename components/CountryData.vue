<template>
  <div style="box-shadow: 0 0 5px rgb(0 0 0 / 30%)">
    <div class="container c2">
      <div class="form-c1">
        <i><fa class="search-icon" icon="magnifying-glass" /></i>
        <input
          v-model="search"
          type="text"
          placeholder="Search For Country..."
        />
      </div>
      <div class="drop1">
        <div class="drop2">
          <p>filter by region</p>
          <select v-model="regions" style="border: 0; background-color: white">
            <option v-for="country in countryInfo" :key="country">
              {{ country.region }}
            </option>
          </select>
        </div>
      </div>
    </div>

    <div class="s1">
      <div v-for="country in searchCountry" :key="country" class="countries">
        <router-link
          style="color: black"
          :to="{ path: 'payal/' + country.name + '/SpecificDetail' }"
        >
          <div class="country">
            <div class="country-img">
              <img :src="country.flags.png" alt="not found" />
            </div>
            <div class="countryinfo">
              <h5>
                <b>{{ country.name }}</b>
              </h5>
              <p><strong>Population:</strong>{{ country.population }}</p>
              <p><strong>Region:</strong>{{ country.region }}</p>
              <p><strong>Capital:</strong>{{ country.capital }}</p>
            </div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      countryInfo: [],
      url: 'https://restcountries.com/v2/all',
      search: '',
      regions: '',
    }
  },
  computed: {
    searchCountry() {
      return this.countryInfo
        .filter((country) => {
          return country.name.match(this.search)
        })
        .filter((country) => {
          return country.region.match(this.regions)
        })
    },
  },
  async created() {
    const res = await this.$axios.$get(this.url)
    this.countryInfo = res
  },
}
</script>
