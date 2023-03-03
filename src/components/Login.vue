<script setup>
import { ref } from 'vue'
import { useStore } from 'vuex'
import { useRouter } from 'vue-router'

const email = ref('')
const password = ref('')
const error = ref(null)

const store = useStore()
const router = useRouter()

const Login = async () => {
  try {
    await store.dispatch('logIn', {
      email: email.value,
      password: password.value
    })
    router.push('/')
  }
  catch(err) {
    error.value = err.message
  }
  return { Login, email, password, error }
}
</script>

<template>
  <h1>Inico de sesión</h1>
  <form @submit.prevent="Login">
    <div class="form-group_email">
      <label for="email">Correo</label>
      <input id="form-email_field" name="email" type="email" required v-model="email">
    </div>
    <div class="form-group_password">
      <label for="password">Contraseña</label>
      <input id="form-password_field" name="password" type="password" required v-model="password">
    </div>
    <div class="form-group_button">
      <button type="submit">Iniciar sesión</button>
    </div>
  </form>
  <RouterView />
</template>

<style>

</style>