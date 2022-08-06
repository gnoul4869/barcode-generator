<script setup lang="ts">
// import VueBarCode from '@chenfengyuan/vue-barcode';
import { ref } from 'vue';

const BarcodeValue = ref('');
</script>

<template>
    <form class="form">
        <h2>Type to generate</h2>

        <input type="text" v-model="BarcodeValue" />

        <button v-if="BarcodeValue">Save Barcode</button>
    </form>
</template>

<style scoped>
.form {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}

.form h2 {
    color: mediumspringgreen;
}

button {
    height: 40px;
    width: 310px;
    background-color: green;
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-size: medium;
    display: block;
    margin-top: 1.3rem;
}

input {
    height: 30px;
    width: 300px;
    padding: 5px;
    font-size: 1rem;
    border-radius: 7px;
}
</style>
