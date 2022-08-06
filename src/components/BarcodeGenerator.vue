<script setup lang="ts">
import { ref, watch } from 'vue';
import JsBarcode from 'jsbarcode';
import html2canvas from 'html2canvas';

const barcodeContainer = ref(null);
const barcodeSVG = ref(null);
const barcodeValue = ref('');

const error = ref('');

watch(barcodeValue, (value) => {
    if (barcodeSVG.value && value) {
        JsBarcode(barcodeSVG.value, value, {
            width: 3,
            height: 80,

            fontOptions: 'bold',
        });
    }
});

const submitHandler = async () => {
    if (barcodeContainer.value) {
        try {
            const canvas = await html2canvas(barcodeContainer.value);
            const imgData = canvas.toDataURL('image/png');
            const link = document.createElement('a');
            link.download = `barcode_${barcodeValue.value}.png`;
            link.href = imgData;
            link.click();
        } catch (err) {
            error.value = 'Oops, something went wrong';
        }
    }
};
</script>

<template>
    <form class="form" @submit.prevent="submitHandler">
        <h3 v-if="!barcodeValue">Type to generate barcode</h3>

        <div ref="barcodeContainer" class="barcodeContainer">
            <svg v-show="barcodeValue" ref="barcodeSVG"></svg>
        </div>

        <input type="text" v-model="barcodeValue" />

        <button v-if="barcodeValue" type="submit">Save</button>
        <h4 v-if="error" class="error">{{ error }}</h4>
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
    margin-top: 1rem;
    transition: border-color 0.2s ease-in-out;
}

input:focus {
    border-color: mediumaquamarine;
}

.error {
    color: tomato;
}
</style>
