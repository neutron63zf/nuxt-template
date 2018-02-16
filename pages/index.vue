<template lang="pug">
section.container
  img(
    src="~assets/img/logo.png"
    alt="Nuxt.js Logo"
  ).logo
  h1 USERS
  ul.users
    li(
      v-for="(user, index) in users"
      :key="index"
    ).user
      nuxt-link(:to="{ name: 'id', params: { id: index }}")
        |{{ user.name }}
  hr
  nuxt-link(to="todos")
    |store todo sample
</template>

<script>
import axios from '~/plugins/axios'

export default {
  async asyncData () {
    let { data } = await axios.get('/api/users')
    return { users: data }
  },
  head () {
    return {
      title: 'Users'
    }
  }
}
</script>

<style lang="scss" scoped>
.title
{
  margin: 30px 0;
}
.users{
  list-style: none;
  margin: 0;
  padding: 0;
  .user{
    margin: 10px 0;
  }
}
</style>
