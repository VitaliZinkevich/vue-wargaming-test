<template>
<div>
    <Currency/>
    <el-table
            :data="tableData"
            style="width: 100%"
            :border="true"
            :stripe="true"

    >

        <el-table-column
                prop="transaction_id"
                label="Transaction_id"
                sortable
                >
        </el-table-column>

        <el-table-column
                label="Created_at"
                min-width="90"
                sortable
                prop="created_at"

                 >
            <template slot-scope="scope">
                {{ scope.row.created_at | timeStampToFormatDate}}
            </template>

        </el-table-column>

        <el-table-column
                min-width="180"
                label="User_id"

                >

                <template slot-scope="scope">
                    <user-info :user="scope.row.user_id"  ></user-info>
                </template>

        </el-table-column>

        <el-table-column
                prop="total"
                label="Total"
                sortable
        >
        </el-table-column>


        <el-table-column
                prop="card_type"
                label="Card_type"
                sortable
        >
        </el-table-column>

        <el-table-column
           label="Card_number">
           <template slot-scope="scope">
                {{ scope.row.card_number | hideNumber}}
           </template>

        </el-table-column>

        <el-table-column
            label="Location"
            sortable
            prop="order_country"

        >

            <template slot-scope="scope">

                    {{ scope.row.order_country }}
                <br>
                    ({{ scope.row.order_ip }})

            </template>

        </el-table-column>

    </el-table>

</div>
</template>

<script>
import data from '../data/orders.json'
import UserInfo from './UserInfo.vue'
//import Statistics from './Statistics.vue'
import Currency from './Currency.vue'

export default {
  name: 'app-table',
  data () {
    return {
        tableData: data,
    }
  },
  components:{
      'user-info': UserInfo,

      Currency,



  },
  method:{

  },
  filters: {
      hideNumber: (value)=>{
          return value.slice (0, 2)+'********'+value.slice (-4)
      },
      timeStampToFormatDate: (value)=>{
          // DD/MM/YYYY hh:mm:ss
          let date = new Date(value*1000);

          var hours = '0'+date.getHours();
          var minutes = "0" + date.getMinutes();
          var seconds = "0" + date.getSeconds();

          var dateN = "0" + date.getDate();
          var month = "0" + (date.getMonth()+1);
          var year = date.getFullYear()

          var formatedStamp = dateN.substr(-2)+'/'+month.substr(-2)+'/'+year+' '+hours.substr(-2) + ':' + minutes.substr(-2) + ':' + seconds.substr(-2);

          return formatedStamp
      }

  }
  }
  

</script>

<style scoped>

</style>
