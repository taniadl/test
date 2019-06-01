<template>
  <div id="app">
    <div id="nav">
      <h1> My cool planner</h1>
      <router-link to="/about">About</router-link>
    </div>
    <router-view></router-view>

  </div>
</template>

<script>

</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Indie+Flower|Roboto+Mono&display=swap');

#nav {
  background-image: url(./assets/galaxy_navi.jpg);
  background-size: cover;
  padding: 40px;
  text-align: left;
}

#nav h1{
  color: white;
  font-family: 'Indie Flower', cursive;
  font-size: 60px;
}
</style>
