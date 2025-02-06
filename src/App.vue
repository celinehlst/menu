<script setup>
import data from './data.json'

const dataBase = data
console.log(dataBase[2].author.name)
</script>

<template>
  <header>
    <button v-for="element in dataBase" :key="element.id">
      {{ element.title }} ({{ element.category }})
    </button>
  </header>
  <section>
    <h1>Faites votre choix</h1>
  </section>
  <section v-for="element in dataBase" :key="element.id">
    <h2>{{ element.title }}</h2>
    <p v-if="element.synopsis">{{ element.synopsis }}</p>
    <p v-if="element.content">{{ element.content }}</p>
    <p v-if="element.author.name">{{ element.author.name }}</p>
    <p v-else>{{ element.author }}</p>
  </section>
</template>

<style scoped>
button {
  margin: 0px 20px;
}

section {
  margin: 50px 0px;
}
</style>
