<template>
  <div>
    <h2>Orders</h2>
    <div v-if="orders">
      <div>Orders: {{ orders}}</div>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      orders:null ,
    }
  },
  apollo: {
    orders: gql`query {
      orders(startDate: "01/01/2022", endDate: "01/01/2023") {
        id
        orderName
        orderDate
        currency
        total
        details {
          id
          product {
            id
            description3
            isFavorites
          }          
          quantity
          price
          total
        }
      }
    }
    `
  }
}
</script>

