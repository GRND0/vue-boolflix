<template>
  <div id="app">
    <FlixHeader @search="ricercaDati($event)" />
    <FlixMain :items='movies' /> <!-- passo movies -->
  </div>
</template>

<script>
import FlixHeader from "./components/FlixHeader.vue";
import FlixMain from "./components/FlixMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    FlixHeader,
    FlixMain,

  },
  data: function () {
    return {
      movies: [],
    }
  },
  methods: {
    ricercaDati(query) {
      axios
        .get('https://api.themoviedb.org/3/search/movie?', {
          params: {
            api_key: '278df2843e911190453b62b7973fd96e',
            query: query
          }
        })
        .then((resp) => {
            console.log(resp);
            this.movies = resp.data.results;
          });
    },
  },
};
</script>

<style lang="scss">
</style>
