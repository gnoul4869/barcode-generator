<script setup lang="ts">
import BarcodeGenerator from '@/components/BarcodeGenerator.vue';
</script>

<template>
    <header>
        <h1 class="title">- Barcode Generator -</h1>
    </header>

    <main>
        <BarcodeGenerator />
    </main>
</template>

<style>
.title {
    text-align: center;
}
</style>
