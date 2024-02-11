<script>
import { pics } from '../data';

export default {
    name: 'ProductionCard',
    props: {
        production: Object,
    },
    computed: {
        title() {
            return this.production.title || this.production.name;
        },
        originalTitle() {
            return this.production.original_title || this.production.original_name;
        },
        hasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.production.original_language);
        },
        flagSrc() {
            const url = new URL(`../assets/img/${this.production.original_language}.png`, import.meta.url);
            return url.href;
        },
        posterSrc() {
            return this.production.poster_path ? pics.baseUri + this.production.poster_path : pics.placeholder;
        },
        vote() {
            return Math.ceil(this.production.vote_average / 2);
        },
    },
};
</script>


<template>
    <div class="card mx-3 my-4 d-flex text-center border-0 position-relative">
        <div class="image-container position-relative overflow-hidden">
            <img :src="posterSrc" class="img-card object-fit-fill" />
            <div
                class="card-info w-100 h-100 top-0 end-0 position-absolute d-flex align-items-center justify-content-center">
                <ul class="list-unstyled p-0 m-0">
                    <li>Titolo: {{ title }}</li>
                    <li>Titolo originale: {{ originalTitle }}</li>
                    <li>Trama: {{ production.overview }}</li>
                    <li>
                        Voto : <i v-for="n in 5" :key="n" class="fa-star" :class="n <= vote ? 'fas' : 'far'"></i>
                    </li>
                    <li>
                        <img class="img-flag" v-if="hasFlag" :src="flagSrc" :alt="production.original_language" />
                        <span v-else>{{ production.original_language }}</span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    border-radius: 15px;
    cursor: pointer;

    .image-container {
        border-radius: 15px;
        transition: transform 0.3s ease-in-out;

        &:hover {
            transform: scale(1.1);
        }

        .img-card {
            max-width: 100%;
            height: 400px;
        }

        .card-info {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            opacity: 0;
            transition: opacity 0.3s ease-in-out;

            ul {
                list-style: none;
                padding: 0;
                margin: 0;

                li {
                    font-size: 10px;
                    margin-bottom: 5px;
                    padding: 0 20px 0 20px;

                    .fa-star {
                        font-size: 14px;
                        color: orange;
                    }
                }
            }
        }

        &:hover .card-info {
            opacity: 1;
        }
    }
}

.img-flag {
    height: 50px;
}
</style>