<template>
  <div class="user">
    <h3>{{ name }}</h3>
    <h4>@{{ username }}</h4>
    <p>Email : {{ email }}</p>
    <p><router-link to="/">List of users</router-link></p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data ({ params, error }) {
    return axios.get(`http://jsonplaceholder.typicode.com/users/${params.id}`)
    .then((res) => res.data)
    .catch(() => {
      error({ message: 'User not found', statusCode: 404 })
    })
  }
}
</script>

<style scoped>
.user {
  text-align: center;
  margin-top: 100px;
  font-family: sans-serif;
}
</style>
