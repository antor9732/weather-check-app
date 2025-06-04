<script>
export default {
  name: 'App',
  data() {
    return {
      api_key: 'e8d61496ac0d1816f163083369dcef6c',
      url_base: 'https://api.openweathermap.org/data/2.5/weather',
      query: '',
      weather: {},

    }
  },
  methods: {
    fetchWeather(event) {
      if (event.key === 'Enter') {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
        .then(res => {
          return res.json();
        }).then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    }

  }
}
</script>

<template>
  <main>
    <div class="search-box">
      <input
        type="text"
        class="search-bar"
        placeholder="Search..."
        v-model="query"
        @keypress="fetchWeather"
      />
    </div>

    <div class="weather-wrap">
      <div class="location-box">
        <div class="location">Dhaka, Bangladesh</div>
        <div class="date">Monday, 1st January 2024</div>
      </div>
    </div>

    <div class="weather-box">
      <div class="temp">9°C</div>
      <div class="weather">Rain</div>
    </div>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "montserrat", sans-serif;
}
#app {
  background-image: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}
main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  );
}

.search-box {
  width: 100%;
  margin-bottom: 30px;
}
.search-box .search-bar {
  width: 100%;
  display: block;
  padding: 15px;

  border: none;
  outline: none;
  background: none;
  appearance: none;

  font-size: 20px;
  color: #292929;

  background-color: rgba(255, 255, 255, 0.63);
  border-radius: 0px 16px 0px 16px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  transition: 0.4s;
}

.search-box .search-bar:focus {
  background-color: rgba(255, 255, 255, 0.8);
  box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.2);
  border-radius: 16px 0px 16px 0px;
}

.location-box .location {
  font-size: 30px;
  color: #fff;
  font-weight: 600;
  text-align: center;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.location-box .date {
  font-size: 18px;
  font-weight: 300;
  color: #fff;
  text-align: center;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  font-size: 60px;
  color: #fff;
  padding: 10px 25px;
  display: inline-block;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.5);
  background-color: rgba(255, 255, 255, 0.2);
  border-radius: 16px;
  margin: 20px 0px;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  font-size: 48px;
  color: #fff;
  font-style: italic;
  font-weight: 700;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}
</style>
