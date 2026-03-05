<script setup lang="ts">
import { ref } from 'vue';
import TranslateBox from './components/TranslateBox.vue';
const translateLang = ref("en")
const targetLang = ref("ar")

const result: string = ref("")


</script>

<template>
  <main class="h-full grid">
    <h1 class="text-white font-bold text-center w-screen flex justify-center items-center">AJS Translate</h1>

 <section class="md:flex h-fit  justify-center gap-x-4 max-md:grid max-md:content-center items-center">
  <TranslateBox :editable="false" v-model="result"></TranslateBox>
  <TranslateBox :editable="true" v-model="result"></TranslateBox>
 </section>
 </main>
</template>

<style scoped></style>
