<template>
    <th >
        <td v-for="header in headers"> {{header}}</td>
    </th>
</template>

<script>


export default {
  name: 'app-table-headers',
  data () {
    return {
        
    headers: [
        "transaction_id", 
        "created_at",
        "user_id",
        "total",
        "card_type",
        "card_number",
        "location",

        ]
    }
  },
  components:{},
  methods: {

       
    },

  }
  

</script>

<style scoped>

</style>
