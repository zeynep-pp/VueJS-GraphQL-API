<template>
  <div>
    <h2>Orders</h2>
  <table class="table is-striped is-narrow is-hoverable is-fullwidth">
  <thead>
    <tr>
      <th>Order Name</th>
      <th>Date</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    <tr
      v-for="orders in orders"
      :key="orders.id">
      <td>{{ orders.orderName }}</td>
      <td>{{ orders.orderDate }}</td>
      <td>{{ orders.total }}</td>
    </tr>
  </tbody>
  </table>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      orders: [],
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

