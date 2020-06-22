<template>
  <div id="app">
      <h1>
          <router-link to="/"><i class="las la-home"></i></router-link>
          <span class="ml-3">My app</span>
      </h1>
      <hr>
      <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
    .la-home {
        font-size: 24px;
        color: black;
        width: 26px;
    }
    .la-home:hover {
        font-size: 26px;
        color: blue;
    }
</style>
