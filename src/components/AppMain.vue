<script>
import ProductionSection from './ProductionSection.vue'
export default {
    name: 'AppMain',
    components: { ProductionSection }
}
</script>

<template>
    <ProductionSection collection="movies" />
    <ProductionSection collection="series" />
</template>

<style></style>