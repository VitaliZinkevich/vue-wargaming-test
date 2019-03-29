<template>
    <tbody>

    <tr v-for="order in orders">
        <td>{{order.transaction_id}} </td>
        <td>{{order.created_at}} </td>
        <td>{{order.user_id}} </td>
        <td>{{order.total}} </td>
        <td>{{order.card_type}} </td>
        <td>{{order.card_number}} </td>
        <td>
            {{order.order_country}}
            {{order.order_ip}}
        </td>
    </tr>

    </tbody>
</template>


<script>


export default {
  name: 'app-table-row',
  data () {
    return {
        
    }
  },
  props: {
     orders:{
        type: Array,
        required : true
     }
  }

  
}
</script>

<style scoped>

</style>
