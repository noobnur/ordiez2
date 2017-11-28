<!-- src/components/Orders.vue -->
<template>
<table class="table table-hover product-table">
  <thead>
    <tr>
      <th>Order ID</th>
      <th>Feedback</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="order in orders" track-by="id">
        <td>{{order.order_id}}</td>
        <td>Feedback</td>
      </tr>

      <!-- <p>
        {{orders}}
      </p> -->
  </tbody>
</table>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      orders: [],
      errors: []
    }
  },

  created() {
axios.get('https://stormy-earth-22350.herokuapp.com/orders')
.then(response => {
  this.orders = response.data
  })
  .catch(function(error) {
    console.log(error);
  });

}
}
</script>
