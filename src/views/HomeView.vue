<template>
  <main>
    <pre>
      <button @click="post">Start</button>
    </pre>
  </main>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'

export default {
  setup () {
    const config = {
      params: {
        _limit: 5
      }
    }
    const record = ref({
      id: 1,
      title: 'foo',
      body: 'bar',
      userId: 1
    })

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
      try {
        const { data } = await axios.post('https://jsonplaceholder.typicode.com/posts', record.value)
      } catch (error) {
        throw new Error(error)
      }
    }

    const put = async () => {
      try {
        return await axios.put('https://jsonplaceholder.typicode.com/posts/1', record.value)
      } catch (error) {
        throw new Error(error)
      }
    }

    const remove = () => {
      try {
        const data = axios.delete('https://jsonplaceholder.typicode.com/posts/2')
      }catch (error) {
        throw new Error(error)
      }
    }

    return {
      get,
      post,
      put,
      remove,
      record
    }
  }
}
</script>
