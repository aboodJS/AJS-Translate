<script setup lang="ts">
const props = defineProps({
  editable: Boolean,

})
const text = defineModel()



</script>

<template>
  <div class="opacity-95 grid justify-center border-gray-700 rounded-xl border bg-gray-900  opacity-95 h-65 outline-0 w-96">
    <textarea v-model="text" :disabled="props.editable"  @change="() => console.log(text)" class="indent-2 text-white opacity-95 h-64 outline-0 w-96 " name="" id="" maxlength="500"></textarea>

  </div>
</template>
