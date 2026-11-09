<template>
    <div class="groupContainer" id="shoppingListInfo">
        <table>
            <tr>
                <th>Product</th>
                <th class="price">Prijs</th>
                <th>Hoeveelheid</th>
                <th class="price">Subtotaal</th>
            </tr>
            <tr v-for="(product, index) in calculatedProducts" :key="product.productName">
                <td>{{ product.productName }}</td>
                <td>€{{ product.productPrice.toFixed(2) }}</td>
                <td><input type="number" v-model="shoppingListProducts[index].productQuantity" /></td>
                <td>€{{ product.productSubTotal.toFixed(2) }}</td>
            </tr>
            <tr>
                <td colspan="3" id="totalCost">Totaal</td>
                <td>€{{ calculatedTotal.toFixed(2) }}</td>
            </tr>
        </table>
    </div>
</template>

<script setup>
import {computed} from 'vue';

const props = defineProps({
    shoppingListProducts: Object,
});

const calculatedProducts = computed(() => {
    return props.shoppingListProducts.map(product => ({
        ...product,
        productSubTotal: product.productPrice * product.productQuantity,
    }));
});

const calculatedTotal = computed(() => {
    let total = 0;
    for (let x in props.shoppingListProducts) {
        total += calculatedProducts.value[x].productSubTotal;
    }
    return total;
});
</script>
