<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 18 ? 'warm' : ''">
    <main>

      <div class="search-box">
        <input type="text"  class="search-bar" placeholder="Search..." v-model="query" @keypress="fetchWeather">

      </div>

      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">

        <div class="location-box">
          <div class="location">{{weather.name}}</div>
          <div class="date">{{dateBuilder()}}</div>
        </div>

        <div class="weather-box">
          <div class="temp">{{Math.round(weather.main.temp)}}°c</div>
          <div class="weather">{{weather.weather[0].main}}</div>
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
      url_base:"https://api.openweathermap.org/data/2.5/",
      query:"",
      weather:{}
    }
  },
  methods: {
    fetchWeather(e) {
      if(e.key === "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
            .then(res => {
              return res.json()

            })
            .then(this.setResults)
      }

    },
    setResults(results) {
      this.weather = results
      console.log(results)

    },
    dateBuilder() {
      let d = new Date()

      let months = ["January","February","March","April","June","July","August","September","October","November","December"]
      let days = [ "Monday","Tuesday","Wednesay","Thursday","Friday","Saturday","Sunday"]


      let day = days[d.getDay()]
      let date = d.getDate()
      let month = months[d.getMonth()]
      let year = d.getFullYear()


      return `${day} ${date} ${month} ${year}`
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

#app.warm {
  background-image: url("./assets/warm-bg.jpg");
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