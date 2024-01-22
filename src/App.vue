<template>
  {{ user.first_name }} {{ user.last_name }}
  <br>
  {{ admin.first_name }} {{ admin.last_name }}
  <img @click="changeName()" alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import { reactive, ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup() {
    const user = reactive({
      first_name: 'Jhon',
      last_name: 'Snow'
    })

    const admin = ref({
      first_name: 'Master',
      last_name: 'User'
    })

    let name = 'Alessandro'

    const changeName = () => {
      alert('chegou')
      name = 'Jhon Snow'
      user.first_name = 'Sansa'
      admin.value.first_name = 'Main' // usar .value para reatividade
    }
    return {
      user,
      name,
      admin,
      changeName
    }
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
