<template>
    <div class="item">
        <h3>{{ props.name }}</h3>
        <h4>{{ props.category }}</h4>
        <p>Precio: {{ props.price }}</p>
        <p>Unidades: {{ props.units }}</p>
    </div>
</template>

<script lang="ts" setup>
    import { defineProps } from "vue";

    // PROPS QUE NOS PASA EL PADRE (ItemsList)
    const props = defineProps(
        {
            name: {type: String, required: true},
            category: {type: String, required: true},
            price: {type: Number, required: true},
            units: {type: Number, required: true},
        }
    );
</script>

<style scoped>
    .item {
        background-color: #e3e3d1;
        border-radius: 15px;
        padding: 10px;
        height: 180px;
    }
</style>