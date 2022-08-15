<template>
  <div>
    <h2>Products</h2>
      <table class="table is-striped is-narrow is-hoverable is-fullwidth">
  <thead>
    <tr>
      <th>Description</th>
      <th>Barcode</th>
      <th>Favorite</th>
    </tr>
  </thead>
  <tbody>
    <tr
      v-for="products in products.products"
      :key="products.id">
      <td>{{ products.description3 }}</td>
      <td>{{ products.barcode1 }}</td>
      <td>{{ products.isFavorites}}</td>
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
      products: [],
    }
  },
  apollo: {
    products: gql`query {
      products(
          index: 5
          limit: 10
      ) {
      count
      products {
          id
          description3
          barcode1
          isFavorites
          price {
              price {
                  priceId
                  price
                  parcelPrice
                  discount
                  netPrice
                  netParcelPrice
              }
          }
          stockStatus {
              available
          }
          webPublished
          mobilePublished
          }
      }
    }
    `
  }
}
</script>

