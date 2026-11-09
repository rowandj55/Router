<template>
    <GroceriesTable :shoppingListProducts="shoppingListProducts" />
</template>

<script setup>
import GroceriesTable from '../components/GroceriesTable.vue';

import {ref} from 'vue';

const shoppingListProducts = ref([
    {
        productName: 'Rijst',
        productPrice: 1,
        productQuantity: 0,
        productSubTotal: 0,
    },
    {
        productName: 'Broccoli',
        productPrice: 0.99,
        productQuantity: 0,
        productSubTotal: 0,
    },
    {
        productName: 'Koekjes',
        productPrice: 1.2,
        productQuantity: 0,
        productSubTotal: 0,
    },
    {
        productName: 'Noten',
        productPrice: 2.99,
        productQuantity: 0,
        productSubTotal: 0,
    },
]);
</script>
