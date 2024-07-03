<template>
    <div class="main-wrapper">
        <section>
            <ItemGenerator @addItem="añadirItem"></ItemGenerator>
        </section>
        <section>
            <ul class="item-list">
                <li v-for="(elm, index) in items" :key="index">
                    <ItemDetail :name="elm.name" :category="elm.category" :price="elm.price" :units="elm.units"></ItemDetail>
                </li>
            </ul>
        </section>
    </div>
</template>

<script lang="ts" setup>
    import { Ref, ref } from "vue";
    import ItemGenerator from './ItemGenerator.vue';
    import ItemDetail from './ItemDetail.vue';

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