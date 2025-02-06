<script setup>
import { ref, computed } from 'vue'
import dataBase from './data.json'

const displayMessage = ref(true)
const displayElement = ref(false)

let selection = ref({})

const changeInfos = (element) => {
  selection.value = element
  displayMessage.value = false
  displayElement.value = true
}

const averageRate = computed(() => {
  let total = 0
  for (let i = 0; i < selection.value.rates.length; i++) {
    total += selection.value.rates[i]
  }
  const numOfrates = selection.value.rates.length
  return total / numOfrates
  // dataBase[index].rates.length
})

console.log(selection.value)
</script>

<template>
  <header>
    <button v-for="element in dataBase" :key="element.id" @click="changeInfos(element)">
      {{ element.title }} ({{ element.category }})
    </button>
  </header>
  <section>
    <h1 v-show="displayMessage">Faites votre choix</h1>
  </section>
  <section class="content" v-show="displayElement">
    <h2>{{ selection.title }}</h2>
    <p>{{ selection.synopsis }}</p>
    <p>{{ selection.content }}</p>
    <p v-if="selection.category === 'article' && selection.author">{{ selection.author.name }}</p>
    <p v-if="selection.category === 'livre'">{{ selection.author }}</p>
    <!-- <p v-else>{{ selection.author }}</p> -->
    <p>Pas encore de like {{ selection.rates }}</p>
    <p>Pas encore de like {{ averageRate }}</p>
  </section>
</template>

<style scoped>
button {
  margin: 0px 20px;
}

section {
  margin: 50px 0px;
}

.content {
  background: rgb(233, 197, 121);
  border-radius: 20px;
  padding: 10px;
}
</style>
