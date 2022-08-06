<script setup lang="ts">
import { ref, watch } from 'vue';
import JsBarcode from 'jsbarcode';

const barcode = ref(null);
const barcodeValue = ref('');

watch(barcodeValue, (value) => {
    if (barcode.value && value) {
        JsBarcode(barcode.value, value, {
            width: 3,
            height: 80,
            fontOptions: 'bold',
        });
    }
});
</script>

<template>
    <form class="form">
        <h3 v-if="!barcodeValue">Type to generate barcode</h3>

        <svg v-show="barcodeValue" ref="barcode"></svg>

        <input type="text" v-model="barcodeValue" />

        <button v-if="barcodeValue">Save</button>
    </form>
</template>

<style scoped>
.form {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}

svg {
    margin-bottom: 4rem;
}

button {
    height: 4rem;
    width: 31rem;
    background-color: mediumaquamarine;
    border: none;
    border-radius: 0.5rem;
    font-size: medium;
    display: block;
    margin-top: 1.3rem;
    color: #444;
    font-weight: 600;
    cursor: pointer;
}

input {
    height: 3rem;
    width: 30rem;
    padding: 0.5rem;
    font-size: 1rem;
    border-radius: 0.7rem;
    outline: none;
    transition: border-color 0.2s ease-in-out;
}

input:focus {
    border-color: mediumaquamarine;
}
</style>
