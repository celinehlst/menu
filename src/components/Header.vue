<script setup>
const props = defineProps({
  dataBase: Array,
})
const emit = defineEmits(['changeInfos'])
</script>
<template>
  <header>
    <button v-for="element in dataBase" :key="element.id" @click="$emit('changeInfos', element)">
      {{ element.title }} ({{ element.category }})
    </button>
  </header>
</template>
<style scoped></style>
