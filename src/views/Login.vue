<template>
  <div>
    <form action="" method="POST" @submit.prevent="login">
      <div>
        <input type="email" v-model="email" name="email" id="email" placeholder="Email">
      </div>

      <div>
        <input type="password" v-model="password" name="password" id="password" placeholder="Enter your password">
      </div>

      <div>
        <button type="submit">Login</button>
      </div>
    </form>
  </div>
</template>

<script>
import gql from 'graphql-tag'
import { onLogin } from '../vue-apollo.js'

export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login() {

      this.$apollo.mutate({
        // Query
        mutation: gql`mutation($email: String!,$password: String!){
          login(
            email: $email, 
            password: $password)
        }`,
        // Parameters
        variables: {     
            email: this.email,
            password: this.password         
        }

      }).then((data) => {
        // Result
        console.log(data)
        onLogin(this.$apollo.provider.defaultClient, data.data.login)
        this.$router.push('/protected')
        // Error
        console.error(error)
        // We restore the initial user input
      })
    },
  },
}
</script>

<style scoped>
  input {
    padding: 14px 20px;
    font-size: 18px;
    margin-bottom: 14px;
  }

  button {
    width: 160px;
    padding: 14px;
    background: #017BFF;
    color: white;
    font-size: 16px;
  }
</style>
