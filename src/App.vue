<template>
  {{ user.first_name }} {{ user.last_name }}
  <br>
  {{ admin.first_name }} {{ admin.last_name }}
  <img @click="changeName()" alt="Vue logo" src="./assets/logo.png">
  <h5>Full Name</h5>
  {{ fullName }}

  <AppButton data-vue="Jon" @update="getUpdate">
    Save
    <template #icon>Icon</template>
  </AppButton>

  <button @click="user.first_name = 'Sansa'">Atualizar</button>
  <AppHook v-if="showAppHook" />
  <button @click="showAppHook = !showAppHook">
    Togle
  </button>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import { reactive, ref, computed, watch } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import AppHook from './components/AppHook.vue'
import AppButton from './components/AppButton.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    AppHook,
    AppButton
},
  
  setup() {
    const user = reactive({
      first_name: 'Jhon',
      last_name: 'Snow'
    })

    const getUpdate = (data) => {
      console.log('getUpdate', data);
    }

    const showAppHook = ref(true)

    const fullName = computed(() =>{
      return `${admin.value.first_name} ${admin.value.last_name}`
    })

    const admin = ref({
      first_name: 'Master',
      last_name: 'User'
    })

    watch(admin, () => {
      console.log('Logica Cabulosa');
    }, {
      deep: true
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
      fullName,
      showAppHook,
      getUpdate,
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
