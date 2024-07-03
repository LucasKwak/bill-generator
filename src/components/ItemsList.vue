<template>
    <div class="main-wrapper">
        <section>
            <ItemGenerator @addItem="añadirItem"></ItemGenerator>
        </section>
    </div>
</template>

<script lang="ts" setup>
    import { Ref, ref } from "vue";
    import ItemGenerator from './ItemGenerator.vue';

    interface IItem {
        name :string,
        category :string,
        price :number,
        units :number
    }

    let items:Ref<Array<IItem>> = ref([]);

    function añadirItem(item:IItem) {
        items.value.push(item);
    }

</script>

<style scoped>
    .main-wrapper {
        display: flex;
        flex-direction: row;
    }
</style>