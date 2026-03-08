<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { useTemplateRef } from "vue";
const props = defineProps({
  editable: Boolean,
  defaultLang: String,

})
const text = defineModel()
const lang = defineModel('lang')

const textArea = useTemplateRef("textBox")

function copyText(): void {
  console.log(textArea.value)

  textArea.value?.select()
  textArea.value?.setSelectionRange(0, 99999)

  navigator.clipboard.writeText(textArea.value?.value)

  console.log(textArea.value?.value)
}



</script>

<template>
  <div class="grid justify-center relative border-gray-700 rounded-xl border bg-gray-900  opacity-95 h-90 max-md:w-[95vw]   outline-0 w-lg">
    <select class="text-white rounded-xl relative h-10 max-md:left-8/12 left-10/12 top-4 bg-[#4f5663] outline-0 w-20"  v-model="lang" name="" id=""><option value="ar">arabic</option>
    <option value="en">english</option>
    <option value="de">german</option></select>
    <textarea v-model="text" ref="textBox" :disabled="props.editable"   class="indent-2 max-md:w-[95vw] text-white opacity-95 h-64 outline-0 w-lg " name="" id="" maxlength="500"></textarea>
      <button @click="copyText" class="bg-gray-800 flex justify-center items-center p-2.5 cursor-pointer absolute top-74 right-10/12 text-white transition-all hover:bg-white hover:text-black rounded-md"><Icon icon="tabler:copy" width="24" height="24"  /></button>
  </div>
</template>
