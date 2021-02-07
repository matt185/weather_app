<template>
  <v-container>
    <h1 class="text-caption-h1 d-flex justify-center">Weather App</h1>
    <v-flex>
      <v-card color="blue-grey darken-2">
        <v-card-text>
          <v-layout justify-center>
            <v-flex class="text-sm-center mb-6">
              <h4>Temperature</h4>
              <h1 class="display-1">{{weather.name}}</h1>
              <img :src="icon" />
              <v-flex class="d-flex flex-column">
                <span class="display-1">{{temp(weather.main.temp)}} &deg;C</span>
                <span>{{weather.weather[0].description}}</span>
              </v-flex>
            </v-flex>
            <v-flex class="text-sm-center mb-6">
              <h4>Wind and Pressure</h4>
              <h4 class="headline mt-2">Wind {{weather.wind.speed}}m/s ({{weather.wind.deg}})&deg;</h4>
              <h4 class="headline mt-4">Humidity {{weather.main.humidity}}%</h4>
              <h4 class="headline mt-4">Pressure {{weather.main.pressure}}hPa</h4>
            </v-flex>
            <v-flex class="text-sm-center mb-6">
              <h4>Other</h4>
              <h5 class="headline mt-2">Max Temperature {{temp(weather.main.temp_max)}} &deg;C</h5>
              <h5 class="headline mt-4">Min Temperature {{temp(weather.main.temp_min)}} &deg;C</h5>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-flex>
    <v-flex class="d-flex justify-center mt-4">
      <v-form class="form" @submit.prevent="setCity">
        <v-text-field v-model="city" label="City Name" placeholder="city name" outlined></v-text-field>
      </v-form>
    </v-flex>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: "London"
    };
  },
  asyncData({ params, $axios }) {
    return $axios
      .$get(
        `https://api.openweathermap.org/data/2.5/weather?q=London&appid=${process.env.ApiKey}`
      )
      .then(res => {
        return { weather: res };
      });
  },
  computed: {
    icon() {
      return this.weather.weather
        ? `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png`
        : "";
    }
  },
  methods: {
    setCity() {
      return this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${process.env.ApiKey}`
        )
        .then(res => {
          this.weather = res;
        });
    },
    temp(temp) {
      return this.weather.main ? Math.round(temp - 273) : "";
    }
  }
};
</script>

<style>
.form {
  width: 50%;
}
</style>