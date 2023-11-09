<template>
  <main>
    <pre>
      <button @click="post">Start</button>
    </pre>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  setup () {
    const config = {
      params: {
        _limit: 5
      }
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

    const post = async () => {
      const record = {
        title: 'foo',
        body: 'bar',
        userId: 1
      }
      try {
        const { data } = await axios.post('https://jsonplaceholder.typicode.com/posts', record)
        return data
      } catch (error) {
        throw new Error(error)
      }
    }

    return {
      get,
      post
    }
  }
}
</script>
