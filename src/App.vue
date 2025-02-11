<script setup>
import { ref, computed } from 'vue'
import dataBase from './data.json'
import Article from './components/Article.vue'
// import Book from './components/Book.vue'
import Header from './components/Header.vue'

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
  if (selection.value.rates && selection.value.rates.length > 0) {
    for (let i = 0; i < selection.value.rates.length; i++) {
      total += selection.value.rates[i]
    }
    const numOfrates = selection.value.rates.length
    return total / numOfrates
  } else {
    return 0
  }
})

// console.log(selection.value)

// export { selection, changeInfos, averageRate, displayElement, displayMessage }
</script>

<template>
  <Header :database="dataBase" @changeInfos="changeInfos" />
  <section>
    <h1 v-show="displayMessage">Faites votre choix</h1>
  </section>
  <Article
    :selection="selection"
    :averageRate="averageRate"
    :displayMessage="displayMessage"
    :displayElement="displayElement"
  />
</template>

<style scoped></style>
