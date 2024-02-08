<script>
import { store } from '../data/store'
export default {
    name: 'ProductionSection',
    data: () => ({ store })
}
</script>

<template>
    <section class="container p-5 text-white">
        <h2>Movies</h2>
        <ul v-for="movie in store.movies" :key="movie.id" class="list-unstyled">
            <li>{{ movie.title }}</li>
            <li>{{ movie.original_title }}</li>
            <li>{{ movie.original_language }}</li>
            <li>{{ movie.vote_average }}</li>
        </ul>
    </section>
</template>

<style></style>
