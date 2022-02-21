<template>
  <div>
    <Navbar />
    <Country-Details />
  </div>
</template>

<script>
import CountryDetails from '~/components/Country-Details.vue';
export default {
  name: "IndexPage",
  components: {CountryDetails },
};
</script>