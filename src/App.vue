<script setup lang="ts">
import { computed, ref, type Ref } from 'vue';
import TranslateBox from './components/TranslateBox.vue';
const translateLang = ref("en")
const targetLang = ref("ar")

const query = ref("")

const result = ref("")

async function translateText(input: string, output: string, data: string) {
  const translation = await fetch(`https://api.mymemory.translated.net/get?q=${data.split(" ").join("_")}&langpair=${input}|${output}`).then(d => d.json())

  if (data === "") {
    result.value = ""
  }
  else {
    result.value = translation.responseData.translatedText
  }



}









</script>

<template>
  <main class="h-full grid">
    <h1 class="text-white font-bold text-center w-screen flex justify-center items-center">AJS Translate</h1>

 <section class="md:flex h-fit justify-center gap-x-4 max-md:grid max-md:content-center items-center">
  <TranslateBox :editable="false" v-model="query"></TranslateBox>
  <TranslateBox :editable="true" v-model="result"></TranslateBox>
  <button class="bg-blue-900" @click="() => {
    translateText(translateLang, targetLang, query)
    }">check</button>
 </section>

 </main>
</template>

<style scoped></style>
