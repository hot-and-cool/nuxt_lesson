<template>
  <section class="container">
    <div>
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.id }}, {{ user.name }}, {{ user.company.name }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
const axios = require('axios')
let url = 'https://jsonplaceholder.typicode.com/usersxxx'

export default {
  asyncData({ params }) {
    return axios.get(url)
      .then((res) => {
        return { users: res.data }
      })
      .catch((e) => {
        // console.log(e.response.status)
        error({ statusCode: e.response.status, message: e.message })
      })
  }
}
</script>
