<template>
  <div class="box">
    <button class="btn btn-secondary btn-sm top-button" @click="backToMainPage">
      <img
        class="left-arrow"
        :src="require('@/static/arrow-back-outline.svg')"
        alt=""
      />
      back
    </button>
    <div class="row">
      <div class="col-lg-6">
        <img
          class="img-size"
          :src="countryDetails[0].flags.png"
          alt="Country-Flag"
        />
      </div>
      <div class="col-lg-6">
        <h1>{{ countryDetails[0].name }}</h1>
        <div class="row">
          <div class="col-lg-6">
            <h3 class="d-inline">Native Name:</h3>
            <p class="d-inline">{{ countryDetails[0].nativeName }}</p>
            <br />
            <h3 class="d-inline">Population:</h3>
            <p class="d-inline">{{ countryDetails[0].population }}</p>
            <br />
            <h3 class="d-inline">Region:</h3>
            <p class="d-inline">{{ countryDetails[0].region }}</p>
            <br />
            <h3 class="d-inline">Sub Region:</h3>
            <p class="d-inline">{{ countryDetails[0].subregion }}</p>
            <br />
            <h3 class="d-inline">Capital:</h3>
            <p class="d-inline">{{ countryDetails[0].capital }}</p>
          </div>
          <div class="col-lg-6">
            <h3 class="d-inline">Top Level Domain:</h3>
            <p class="d-inline">{{ countryDetails[0].topLevelDomain[0] }}</p>
            <br />
            <h3 class="d-inline">Currencies:</h3>
            <p class="d-inline">{{ countryDetails[0].currencies[0].name }}</p>
            <br />
            <h3 class="d-inline">Languages:</h3>
            <p class="d-inline">{{ countryDetails[0].languages[0].name }}</p>
          </div>
        </div>
        <br />
        <br />
        <h3 class="d-inline">Border Countries:</h3>
        <button
          v-for="countryName in countryDetails[0].borders"
          :key="countryName"
          class="d-inline btn btn-secondary btn-sm country-btn"
          :value="countryName"
          @click="getCountriesByCode(countryName)"
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
      countryDetails: [
        {
          name: '',
          nativeName: '',
          population: '',
          region: '',
          subregion: '',
          capital: '',
          topLevelDomain: '',
          currencies: [
            {
              name: '',
            },
          ],
          languages: [
            {
              name: '',
            },
          ],
          flags: {
            png: '',
          },
          borders: [''],
        },
      ],
    }
  },
  created() {
    this.getCountriesDetails()
  },
  methods: {
    async getCountriesDetails() {
      const res = await this.$axios.$get(
        'https://restcountries.com/v2/name/' + this.$route.params.country
      )
      this.countryDetails = res
    },
    async getCountriesByCode(countryName) {
      const res = await this.$axios.$get(
        'https://restcountries.com/v2/name/' + countryName)
      this.countryDetails.name = res[0].name
      this.$router.push('/jeel/'+this.countryDetails.name+'/Details')
    },
    backToMainPage(){
         this.$router.push("/jeel")
    }
  },
}
</script>
<style scoped>
.country-btn {
  margin: auto 1%;
  font-size: 10px;
  color: black;
  background-color: white;
  box-shadow: rgb(0 0 0 / 25%) 0 54px 55px, rgb(0 0 0 / 12%) 0 -12px 30px,
    rgb(0 0 0 / 12%) 0 4px 6px, rgb(0 0 0 / 17%) 0 12px 13px,
    rgb(0 0 0 / 9%) 0 -3px 5px;
  border-style: none;
}

button {
  color: black;
  background-color: white;
  box-shadow: rgb(0 0 0 / 25%) 0 54px 55px, rgb(0 0 0 / 12%) 0 -12px 30px,
    rgb(0 0 0 / 12%) 0 4px 6px, rgb(0 0 0 / 17%) 0 12px 13px,
    rgb(0 0 0 / 9%) 0 -3px 5px;
  border-style: none;
}

.left-arrow {
  height: 15px;
}

.top-button {
  margin-bottom: 5%;
}

.box {
  color: black;
  padding: 3%;
  background-color: white;
  padding-bottom: 22.1%;
}

h3 {
  font-size: 16px;
  color: black;
}

p {
  font-size: 12px;
  color: black;
}

.img-size {
  height: 275px;
  width: 400px;
}
</style>
