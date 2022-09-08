<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text"  class="search-bar" placeholder="Search...">
      </div>
    </main>
  </div>
</template>


<script>
export default {
  name: "app",
  data() {
    return {
      api_key: "7b0c56e98922c66a4ff518eb0b8b3ccd",
    }
  }
}


</script>


<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Montserrat', sans-serif;
}

#app {
  background-image: url("./assets/cold-bg.jpg");
}

</style>