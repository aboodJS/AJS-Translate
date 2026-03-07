<script setup lang="ts">
import {  ref, type Ref } from 'vue';
import TranslateBox from './components/TranslateBox.vue';
const translateLang = ref("en")
const targetLang = ref("ar")
const switchedLang = ref("")


const query = ref("")

const result = ref("")

function switchLangs() {
  switchedLang.value = translateLang.value
  translateLang.value = targetLang.value
  targetLang.value = switchedLang.value
}

async function translateText(inputLang: string, outputLang: string, str: string) {
  const translation = await fetch(`https://api.mymemory.translated.net/get?q=${str.split(" ").join("%20")}&langpair=${inputLang}|${outputLang}`).then(d => d.json())


  if (str === "") {
    result.value = ""
  }
  else {
    result.value = translation.responseData.translatedText
  }



}

</script>

<template>
  <main class="h-screen  grid">
    <h1 class="text-white font-bold text-center w-screen flex justify-center items-center">AJS Translate</h1>
<button class="self-center max-md:my-4 justify-self-center cursor-pointer bg-[#3762e4] py-2.5 px-5 rounded-lg text-[#d7def8] border-[0.5px] border-[#5984ec] font-bold" @click="switchLangs">switch languages</button>
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
