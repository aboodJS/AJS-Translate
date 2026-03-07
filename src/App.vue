<script setup lang="ts">
import {  ref, type Ref } from 'vue';
import TranslateBox from './components/TranslateBox.vue';
import { Translator, Credentials } from '@translated/lara';
const translateLang = ref("en-US")
const targetLang = ref("ar-SA")

const creds = new Credentials(import.meta.env.VITE_API_ID, import.meta.env.VITE_API_KEY)
const lara = new Translator(creds)

const query = ref("")

const result = ref("")

async function translateText(inputLang: string, outputLang: string, str: string) {
  const translation = await lara.translate(str, inputLang, outputLang)

  if (str === "") {
    result.value = ""
  }
  else {
    result.value = translation.translation
  }



}

</script>

<template>
  <main class="h-screen  grid">
    <h1 class="text-white font-bold text-center w-screen flex justify-center items-center">AJS Translate</h1>

 <section class="md:flex h-fit justify-center gap-x-4 max-md:grid max-md:gap-y-3 max-md:content-center items-center">
 <div class="relative">
   <TranslateBox v-model:lang="translateLang" :editable="false" v-model="query"></TranslateBox>
   <button class="top-74 right-4 cursor-pointer bg-[#3762e4] py-2.5 px-5 rounded-lg text-[#d7def8] border-[0.5px] border-[#5984ec] font-bold absolute" @click="() => {
    translateText(translateLang, targetLang, query)
    }">Translate</button>
 </div>
  <TranslateBox v-model:lang="targetLang" :editable="true" v-model="result"></TranslateBox>

 </section>

 </main>
</template>

<style scoped></style>
