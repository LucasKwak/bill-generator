<template>
    <div class="main-wrapper">
        <section>
            <ItemGenerator></ItemGenerator>
        </section>
    </div>
</template>

<script lang="ts" setup>
    import ItemGenerator from './ItemGenerator.vue';

</script>

<style scoped>
    .main-wrapper {
        display: flex;
        flex-direction: row;
    }
</style>