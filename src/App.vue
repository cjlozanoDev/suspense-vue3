<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p v-if="error">
    {{ error }}
  </p>
  <Suspense v-else>
    <template #default>
      <HelloWorld />
    </template>
    <template #fallback>
      <p> Loading... </p>
    </template>
  </Suspense>
</template>

<script>
import { ref, onErrorCaptured } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup() {
    const error = ref(null)
    onErrorCaptured(e => {
      error.value = e
      return true
    })

    return { error }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>