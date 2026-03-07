<script setup lang="ts">

const props = defineProps({
  editable: Boolean,
  defaultLang: String,

})
const text = defineModel()
const lang = defineModel('lang')



</script>

<template>
  <div class="grid justify-center relative border-gray-700 rounded-xl border bg-gray-900  opacity-95 h-90 max-md:w-[95vw]   outline-0 w-lg">
    <select class="text-white rounded-xl relative h-10 max-md:left-8/12 left-10/12 top-4 bg-[#4f5663] outline-0 w-20"  v-model="lang" name="" id=""><option value="ar-SA">arabic</option>
    <option value="en-US">english</option>
    <option value="de-GR">german</option></select>
    <textarea v-model="text" :disabled="props.editable"   class="indent-2 max-md:w-[95vw] text-white opacity-95 h-64 outline-0 w-lg " name="" id="" maxlength="500"></textarea>

  </div>
</template>
