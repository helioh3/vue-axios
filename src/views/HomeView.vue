<template>
  <main>
    <pre>
      <button @click="get">Start</button>
    </pre>
  </main>
</template>

<script>
import axios from 'axios'
import { onMounted } from 'vue'

export default {
  setup () {
    const config = {
      params: {
        _limit: 5
      }
    }

    const data = {
      title: 'foo',
      body: 'bar',
      userId: 1
    }

    const get = async () => {
      try {
        const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts', config)
      } catch (error) {
        throw new Error(error)
      }

      // try {
      //   const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5', {})
      // }catch (error) {
      //   throw new Error(error)
      // }
    }
  }
}
</script>
