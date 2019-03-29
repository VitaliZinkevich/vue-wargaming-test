<template>

  <el-row>
    <el-col :span="22" :offset="2">

        <app-table></app-table>

    </el-col>
  </el-row>


</template>

<script>
import Table from './components/Table.vue'

export default {
  name: 'app',
  components: {
    'app-table': Table,
  }
}
</script>

<style scoped>

</style>