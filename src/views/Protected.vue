<template>
  <div>
    <h2>User's Info</h2>
    <div v-if="user">
      <div>User name: {{ user.name }}</div>
      <div>User email: {{ user.email }}</div>
      <div>User code: {{ user.code}}</div>
      <div>User city: {{ user.city }}</div>
      <div>User company name: {{ user.companyName}}</div>
    </div>
    <v-row class="justify-end">
    <router-link to="/orders" tag="button">orders</router-link>
    <router-link to="/products" tag="button">products</router-link>
    </v-row>
    
  </div> 
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      user: null
    }
  },
  apollo: {
    user: gql`query {
      user {
            name
            firebaseUserUID
            code
            contact
            email
            address1
            address2
            address3
            city
            country
            postCode
            telephone
            telephone2
            mobile
            fax
            companyName
            contactName
            contactEmail
            userCode
            creditLimit
            currencyCode
            marketingEmailEnabled
            marketingSmsEnabled
            marketingNotificationEnabled
            showAllPricesIncludingVat
        }
    }
    `
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#navProtected {
  padding: 90px;
}

#navProtected a {
  font-weight: bold;
  color: #2c3e50;
}

#navProtected a.router-link-exact-active {
  color: #42b983;
}
</style>

