<template>
  <div>
    <h2>Orders</h2>
  <b-table class="table is-striped is-narrow is-hoverable is-fullwidth">
  <thead>
    <td>
      <th scope="col">Order Name</th>
      
      

 

    </td>
    <td>
<th scope="col">Date</th>
    </td>
    <td>
<th scope="col">Total</th>
    </td>
            <td>
<th  colspan="2" class="table is-striped is-narrow is-hoverable is-fullwidth">Details</th>
        </td>
      
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css" integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous"></link>
  </thead>
  <tbody>
    <tr 
      v-for="orders in orders"
      :key="orders.id">
      <td>{{ orders.orderName }}</td>
      <td>{{ orders.orderDate }}</td>
      <td>{{ orders.total }}</td>
      <td>
      <div>
          <b-table class="table is-striped is-narrow is-hoverable is-fullwidth"> 
        <tbody>
          <td>
            <tr
              v-for="details in orders.details"
              :key="details.id">
              <td>{{ details.product.description3 }}</td>
              <td>{{ details.price }}</td>
            </tr>
          </td>
        </tbody>
        </b-table>
        </div>
        
      </td>
    </tr>
  </tbody>
  </b-table>
 

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

