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
    fetchProduction(filter) {
      if (!filter) {
        store.movies = [];
        store.series = [];
        return;
      }
      this.fetchApi("search/movie", 'movies', filter);
      this.fetchApi("search/tv", 'series', filter);
    },
    fetchApi(endpoint, collection, filter) {
      const { baseUri, language, apiKey } = api;

      const params = {
        query: filter,
        api_key: apiKey,
        language
      }
      axios.get(`${baseUri}/${endpoint}`, { params })
        .then((res) => {
          store[collection] = res.data.results;
        })
        .catch((err) => {
          console.error(err)
        })
    }
  }
}
</script>

<template>
  <AppHeader @search-term="fetchProduction" />
  <AppMain />
</template>

<style>
body {
  background-color: #565456;
  height: 100vh;
}
</style>
