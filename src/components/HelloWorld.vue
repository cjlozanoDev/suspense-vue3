<template>
  <h1> Hola </h1>
  {{ data }}
</template>

<script>
export default {
  name: 'HelloWorld',
  async setup() {
    const data = await new Promise((resolve, reject) =>
      setTimeout(() => resolve('Algo horrible ha pasado'), 2000)
    )
    return { data }
  }
}
</script>