<template>
    <header>
        <h1>PLATAFORMA PARA CREAR UNA FACTURA</h1>
    </header>
    <main>
        <ItemsList/>
    </main>
</template>

<script lang="ts" setup>
    import ItemsList from './components/ItemsList.vue';
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        margin-top: 20px;
    }

    h1 {
        text-align: center;
    }
</style>
