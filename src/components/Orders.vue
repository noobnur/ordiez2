<!-- src/components/Orders.vue -->
<template>
  <div id="example-2">
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
      <button v-if=!order.feedback v-on:click="greet">Feedback</button>
    </tr>

  </tbody>
</table>
</div>
</template>

<script>
export default {
  data () {
    return {
      orders: [],
      errors: []
    }
  },

  created () {
    axios.get('https://stormy-earth-22350.herokuapp.com/orders')
      .then(response => {
        this.orders = response.data
      })
      .catch(function (error) {
        console.log(error)
      })
  },
  methods: {
    greet: function (event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.name + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
}
</script>
