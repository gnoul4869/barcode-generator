<script setup lang="ts">
import VueBarCode from './components/VueBarCode.vue';
</script>

<template>
    <header>
        <h1 class="title">- Barcode Generator -</h1>
    </header>

    <main>
        <VueBarCode />
    </main>
</template>

<style>
.title {
    text-align: center;
}
</style>
