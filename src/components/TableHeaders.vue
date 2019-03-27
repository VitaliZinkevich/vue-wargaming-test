<template>
    <div >

    </div>
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
        "order_country",
        "order_ip"
        ]
    }
  },
  components:{'add-button': AddButoon},
  methods: {
    addToDoButtonClick: function (){
       
       console.log(this.newToDo)
       this.$emit('readyToAdd', this.newToDo)
       this.newToDo=''
       
    },

  },
  
}
</script>

<style scoped>

</style>
