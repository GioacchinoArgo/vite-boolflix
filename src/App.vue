<script>
import axios from 'axios';
import { api } from './data/index';
import { store } from './data/store';
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
export default {
  name: 'Boolflix',
  components: { AppHeader, AppMain },
  data: () => ({ store }),
  methods: {
    searchMovies(filter) {
      if (!filter) {
        store.movies = [];
        return;
      }

      const { baseUri, language, apiKey } = api;

      const params = {
        query: filter,
        api_key: apiKey,
        language
      }

      axios.get(`${baseUri}/search/movie`, { params })
        .then((res) => {
          store.movies = res.data.results;
        })
        .catch((err) => {
          console.error(err)
        })
    }
  }
}
</script>

<template>
  <AppHeader @search-term="searchMovies" />
  <AppMain />
</template>

<style>
body {
  background-color: #565456;
  height: 100vh;
}
</style>
