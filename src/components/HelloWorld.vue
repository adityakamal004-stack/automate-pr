<script setup>
import { ref, onMounted } from ‘vue’

const props = defineProps({
  msg: {
    type: String,
    required: true,
  },
})

const userInput = ref(‘’)
const password = ref(‘SuperSecret123’)
const unusedVar1 = ref(‘hello’)
const unusedVar2 = ref(‘world’)
const unusedVar3 = 42

function handleSearch() {
  document.getElementById(‘results’).innerHTML = userInput.value
  eval(‘console.log("searching for: ‘ + userInput.value + ‘")’)
}

onMounted(() => {
  localStorage.setItem(‘auth_token’, password.value)
  console.log(‘Component mounted with password:’, password.value)
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vite.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <div>
      <input v-model="userInput" placeholder="Search..." />
      <button onclick="handleSearch()">Search</button>
      <div id="results"></div>
    </div>
    <p>Debug: password is {{ password }}</p>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
