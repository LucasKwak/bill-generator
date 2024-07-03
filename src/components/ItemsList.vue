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
        <p>Total: {{ total }}</p>
        <p>El IVA corresponde a: {{ taxes }}</p>

    </div>
</template>

<script lang="ts" setup>
    import { Ref, ref, computed } from "vue";
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

    const total = computed(
        () => {
            let subtotal = 0;
            for(let i=0; i<items.value.length; i++){
                subtotal = subtotal + items.value[i].price * items.value[i].units;
            }
            return subtotal;
        }
    );

    const taxes = computed(
        () => {
            return total.value * 0.21;
        }
    );

</script>

<style scoped>
    .main-wrapper {
        display: flex;
        flex-direction: row;
    }
</style>