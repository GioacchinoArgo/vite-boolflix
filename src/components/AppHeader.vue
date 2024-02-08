<script>
import SearchForm from './SearchForm.vue'
export default {
    name: 'AppHeader',
    components: { SearchForm },
    emits: ['search-term']
}
</script>

<template>
    <header class="d-flex flex-row align-items-center justify-content-between">
        <h1 class="text-uppercase ms-3">boolflix</h1>
        <SearchForm placeholder="cerca" buttonLabel="cerca" @form-submit="$emit('search-term', $event)" />
    </header>
</template>

<style lang="scss" scoped>
header {
    width: 100%;
    height: 100px;
    background-color: #010001;

    h1 {
        color: #FF0100;
    }
}

.btn-search {
    background-color: #FF0001;
    color: #fff;
    border: none;
}
</style>