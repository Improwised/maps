<template>
  <div class="nav-bar">
    <b-navbar>
      <b-navbar-item class="ml-4 nav-heading"> Where in the world ? </b-navbar-item>
      <b-navbar-nav class="ml-auto">
        <b-nav-item class="mr-4">
          <img src="" alt="">
          <button class="darkmode">Dark Mode</button>
        </b-nav-item>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>
<script>

export default {};
</script>

<style scoped>
.nav-bar{
  background-color: white;
}

.darkmode{
  border-style: none;
  background-color: #2B3743;
  color: white;
}

.nav-heading{
  color: white;
  font-weight: bolder;
}
</style>