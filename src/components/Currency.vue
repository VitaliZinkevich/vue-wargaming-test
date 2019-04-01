<template>
<div>
    <el-select v-model="value" placeholder="Select">

        <el-option
                v-for="(item, key) in options.rates"
                :key="key"
                :label="key + ' ' + item"
                :value="key">
        </el-option>

    </el-select>
    {{value}}
</div>


</template>

<script>

    export default {
        name:'Currency',
        data() {
            return {
                options: {},
                value: ''
                    }
        },
        created: function(){

            this.$http.get ('https://api.exchangeratesapi.io/latest').then ((data)=>{
                //console.log (data.body)
                this.options = data.body
                console.log (data.body.rates)
            })
        }

    }
</script>