<template>
  <div>
    <button class="forb" @click="backToHome">
      <i style="padding-right: 15px"> <fa icon="arrow-left-long" /></i>
      Back
    </button>
    <div class="row">
      <div class="col-md-6">
        <img class="imagebox" :src="countryInfo[0].flags.png" alt="not found" />
      </div>
      <div class="col-md-6 name1">
        <h2>
          <b>{{ countryInfo[0].name }}</b>
        </h2>
        <div class="row">
          <div class="col-lg-6">
            <p><strong>Native Name:</strong> {{ countryInfo[0].nativeName }}</p>

            <p><strong>Population:</strong> {{ countryInfo[0].population }}</p>

            <p><strong>Region:</strong> {{ countryInfo[0].region }}</p>

            <p><strong>Sub Region:</strong> {{ countryInfo[0].subregion }}</p>

            <p><strong>Capital:</strong> {{ countryInfo[0].capital }}</p>
            <br /><br />
          </div>
          <div class="col-lg-6">
            <p>
              <strong>Top Level Domain:</strong>
              {{ countryInfo[0].topLevelDomain[0] }}
            </p>
            <p>
              <strong>Currencies:</strong>
              {{ countryInfo[0].currencies[0].name }}
            </p>
            <p>
              <strong>Languages:</strong>
              {{ countryInfo[0].languages[0].name }}
            </p>
          </div>
        </div>
        <br /><br />
        <strong>Border Countries:</strong>
        <button
          v-for="countryName in countryInfo[0].borders"
          :key="countryName"
          class="b-s"
        >
          {{ countryName }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      countryInfo: [
        {
          topLevelDomain: [],
          currencies: [
            {
              name: [],
            },
          ],
          languages: [
            {
              name: [],
            },
          ],
          flags: {
            png: [],
          },
          borders: [''],
        },
      ],
    }
  },
  async created() {
    const res = await this.$axios.$get(
      'https://restcountries.com/v2/name/' + this.$route.params.country
    )
    this.countryInfo = res
    console.log(this.countryInfo)
  },

  methods: {
    backToHome() {
      this.$router.push('/payal')
    },
  },
}
</script>
