<script setup lang="ts">

const props = defineProps({
  editable: Boolean,
  defaultLang: String,

})
const text = defineModel()
const lang = defineModel('lang')



</script>

<template>
  <div class="grid justify-center border-gray-700 rounded-xl border bg-gray-900  opacity-95 h-90 outline-0 w-lg">
    <select class="text-white rounded-xl relative h-10 left-10/12 top-4 bg-[#4f5663] outline-0 w-20"  v-model="lang" name="" id=""><option value="ar">arabic</option>
    <option value="en">english</option>
    <option value="de">german</option></select>
    <textarea v-model="text" :disabled="props.editable"   class="indent-2 text-white opacity-95 h-64 outline-0 w-lg " name="" id="" maxlength="500"></textarea>

  </div>
</template>
