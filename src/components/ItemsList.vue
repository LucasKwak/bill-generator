<template>
    <div class="main-wrapper">
        <div class="generator-total-wrapper">
            <section>
                <ItemGenerator @addItem="añadirItem"></ItemGenerator>
            </section>
            <section class="total-taxes">
                <p>Total: {{ total }} €</p>
                <p>El IVA corresponde a: {{ taxes }} €</p>
            </section>
        </div>
        <section class="item-list">
            <ItemDetail v-for="(elm, index) in items" :key="index" :name="elm.name" :category="elm.category" :price="elm.price" :units="elm.units"></ItemDetail>
        </section>
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

    // FUNCION A EJECUTAR CUANDO EL HIJO ItemGenerator NOS EMITA EL EVENTO
    function añadirItem(item:IItem) {
        items.value.push(item);
    }

    // DATOS COMPUTADOS
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

    .generator-total-wrapper {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .item-list {
        width: 100%;
        padding: 0 15px 15px 15px;
        gap: 10px;
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    }
</style>