<script setup lang="ts">
// import VueBarCode from '@chenfengyuan/vue-barcode';
import { ref } from 'vue';

const BarcodeValue = ref('');
</script>

<template>
    <form class="form">
        <h2>Type to generate</h2>

        <input type="text" v-model="BarcodeValue" />

        <button v-if="BarcodeValue">Save</button>
    </form>
</template>

<style scoped>
.form {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
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
