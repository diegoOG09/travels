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
    catch (err) {
      error.value = err.message
      console.log(err.value)
    }
    return { Login, email, password, error }
  }
</script>

<template>
  <div class="container login-content">
    <h1>Inicio de sesión</h1>
    <div v-if="error">
      {{ error }}
    </div>
    <form id="login_form" action="#" v-on:submit.prevent="Login">
      <div class="form-group">
        <label id="label_email" for="email">Correo:</label>
        <input
          id="form-email_field"
          name="email"
          type="email"
          required
          autofocus
          placeholder="someone@some.com"
          v-model="email"
        />
      </div>
      <div class="form-group">
        <label id="label_password" for="password">Contraseña:</label>
        <input
          id="form-password_field"
          name="password"
          type="password"
          required
          placeholder="••••••••••••"
          v-model="password"
        />
      </div>
      <div class="form-group_button">
        <button id="login_btn" @click="Login" type="submit">Iniciar sesión</button>
      </div>
    </form>
  </div>
  
</template>

<style lang="scss" scoped>
@import "../styles/variables";
.login-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 25rem;
  margin-top: 3rem;
  margin-bottom: 3rem;
  font-family: $normal-text;
  background-color: $gray;
  border-radius: 10px;
  padding: 2rem 0;

  h1 {
    color: $dark-text;
    margin: 0;
    margin-bottom: 1rem;
  }

  #login_form {
    display: flex;
    flex-direction: column;
    gap: 1rem;

    .form-group {
      display: flex;
      flex-direction: column;
    }
    #label_email {
      margin-right: 3rem;
      color: $dark-text;
    }
    #label_password {
      margin-right: 1rem;
      color: $dark-text;
    }
    input {
      background-color: $gray;
      border-radius: 3px;
      padding: .5rem;
      border: none;
      box-shadow: rgba(0, 0, 0, 0.02) 0px 1px 3px 0px, rgba(27, 31, 35, 0.15) 0px 0px 0px 1px;
      &:focus {
        outline: none;
      }
    }
    .form-group_button {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 1rem;
      #login_btn {
        border: none;
        background-color: $green;
        border-radius: 5px;
        padding: .5rem 1rem;
      }
      
    }
  }
}
</style>