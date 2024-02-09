<script>
import { store } from '../data/store';
import ProductionCard from './ProductionCard.vue';

export default {
    name: 'ProductionSection',
    data: () => ({ store }),
    components: { ProductionCard },
    props: {
        collection: String
    }
};
</script>

<template>
    <section class="container p-5 text-white">
        <h2 class="text-center">{{ collection === 'movies' ? 'Movies' : 'TV Series' }}</h2>
        <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 align-items-center">
            <div class="col text-center" v-for="production in store[collection]" :key="production.id">
                <ProductionCard :production="production" />
            </div>
        </div>
    </section>
</template>
