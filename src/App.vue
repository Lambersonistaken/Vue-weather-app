<template>
  <div id="app">
    <main>

      <div class="search-box">
        <input type="text"  class="search-bar" placeholder="Search...">
      </div>

      <div class="weather-wrap">

        <div class="location-box">
          <div class="location">Northampton, UK</div>
          <div class="date">Monday 20 January 2022</div>
        </div>

        <div class="weather-box">
          <div class="temp">9°c</div>
          <div class="weather">Rain</div>
        </div>

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
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main {
  font-weight: bolder;
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom,rgba(0,0,0,0.25),rgba(0,0,0,0.75));
}

.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  border-radius: 0 16px 0 16px;

  box-shadow: 0 0 8px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.2);
  transition: 0.4s;
}

.search-box .search-bar:focus {
  background-color: rgba(255,255,255,0.7);
  box-shadow: 0 0 16px rgba(0,0,0,0.25);
  border-radius: 16px 0 16px 0;
}


.location-box .location {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0,0,0,0.25);
}

.location-box .date {
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  font-style: italic;
  text-align: center;
}

.weather-box {
  text-align: center;

}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0,0,0,0.25);
  background-color: rgba(255,255,255,0.25);
  border-radius: 16px;
  margin: 30px 0px;

  box-shadow: rgba(0,0,0,0.25);
}


.weather-box .weather {
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow:3px 6px rgba(0,0,0,0.25);
}
</style>