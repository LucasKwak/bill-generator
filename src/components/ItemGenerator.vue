<template>
    <div class="item-generator">
        <h2>AÑADIR UN ITEM</h2>
        <form class="item-form">
            <fieldset class="item-form__wrapper-set">
                <legend>Item a añadir en la factura</legend>
                <div class="item-form__wrapper-input">
                    <label class="item-form__label" for="nombre">Nombre</label>
                    <input class="item-form__input" type="text" id="nombre" v-model="item.name">
                </div>
                <div class="item-form__wrapper-input">
                    <label class="item-form__label" for="categoria">Categoría</label>
                    <select id="categoria" v-model="item.category">
                        <option value="Ocio">Ocio</option>
                        <option value="Trabajo">Trabajo</option>
                        <option value="Normal">Normal</option>
                    </select>
                </div>
                <div class="item-form__wrapper-input">
                    <label class="item-form__label" for="precio">Precio</label>
                    <input class="item-form__input" type="number" id="precio" v-model="item.price">
                </div>
                <div class="item-form__wrapper-input">
                    <label class="item-form__label" for="unidades">Unidades</label>
                    <input class="item-form__input" type="number" id="unidades" v-model="item.units">
                </div>
            </fieldset>
            <button class="form__button" type="button" @click="añadirItem">Añadir item</button>
        </form>
    </div>
</template>

<script lang="ts" setup>
    import { Ref, ref, defineEmits } from "vue";

    interface IItem {
        name :string,
        category :string,
        price :number,
        units :number
    }

    let item :Ref<IItem> = ref(
        {
            name: "",
            category: "Ocio",
            price: 0,
            units: 0
        }
    );

    // EVENTO A EMITIR (LO EMITIMOS AL HACER CLICK EN EL BOTÓN)
    const emit = defineEmits<{
        (e: "addItem", item:IItem): void
    }>();

    // FUNCION A EJECUTAR PARA AÑADIR UN ITEM
    function añadirItem() {
        let tempItem = {
            name: item.value.name,
            category: item.value.category,
            price: item.value.price,
            units: item.value.units,
        }

        // PASAMOS EL ITEM ESPECIFICADO AL PADRE (A LA LISTA PARA QUE LO MUESTRE)
        emit("addItem", tempItem);

        item.value.name = '';
        item.value.category = 'Ocio';
        item.value.price = 0;
        item.value.units = 0;
    }

</script>

<style scoped>
    /*-------------------PARA EL FORMULARIO DE AÑADIR UN ITEM-------------------*/
    .item-generator {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: #b0b087;
        border-radius: 15px;
        padding-bottom: 10px;
    }

    .item-generator h2{
        margin: 0;
    }

    .item-form {
        width: 500px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 15px;
    }

    .item-form__wrapper-set {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
    }

    .item-form__wrapper-input {
        display: flex;
        flex-direction: row;
        width: 400px;
        gap: 40px;
    }

    .item-form__label {
        width: 100px;
    }

    .form__button {
        font-family: Avenir;
        background-color: #58706d;
        color: white;
        border: 1px solid #58706d;
        outline: 0;
    }

    .form__button:hover{
        background-color: white;
        color: #58706d;
        border: 1px solid #58706d;
        box-sizing: content-box;
    }
</style>