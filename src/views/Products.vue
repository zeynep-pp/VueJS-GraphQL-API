<template>
  <div>
    <h2>Products</h2>
    <div v-if="products">
      <div>products: {{ products}}</div>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      products: null
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

