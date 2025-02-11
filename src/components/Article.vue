<script setup>
const props = defineProps({
  selection: Object,
  averageRate: Number,
  displayElement: Boolean,
  displayMessage: Boolean,
})
</script>
<template>
  <section class="content" v-show="displayElement">
    <div v-if="selection.category === 'livre' && selection.numberOfPage < 250">
      <p>Petit livre</p>
    </div>
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
h2 {
  font-size: 30px;
  font-weight: 800;
  margin-bottom: 20px;
}

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
  position: relative;
}

.content div {
  position: absolute;
  right: 0;
  top: -20px;
  background: orange;
  width: 50px;
  height: 50px;
  border-radius: 50px;
  padding: 10px;
  display: flex;
  align-items: center;
}
</style>
