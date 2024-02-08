<script>
export default {
    name: 'SearchForm',
    data: () => ({ searchTerm: '' }),
    props: {
        placeholder: String,
        buttonLabel: String
    },
    emits: ['form-submit']
}
</script>


<template>
    <form @submit.prevent="$emit('form-submit', searchTerm)" class="d-flex align-items-center justify-content-between me-3">
        <input class="border-0 p-1" type="text" :placeholder="placeholder" v-model.trim="searchTerm">
        <button class="btn-search py-1 px-2" type="submit">{{ buttonLabel }}</button>
    </form>
</template>

<style>
.btn-search {
    background-color: red;
}
</style>