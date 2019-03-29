<template>
    <div>
        <el-popover
                placement="bottom"
                trigger="click">

            <div class="user-details">
                <p>Birthday: {{showUserDetalies.birthday | timeStampToFormatDate}}</p>
                <p><img :src="showUserDetalies.avatar" width="100px"></p>
                <p>Company: <a :href="showUserDetalies.company.url" target="_blank">{{showUserDetalies.company.title}}</a></p>
                <p>Industry: {{showUserDetalies.company.industry}} / {{showUserDetalies.company.sector}}</p>
            </div>

            <el-button slot="reference">{{showUserDetalies.fullName}}</el-button>
        </el-popover>
    </div>

</template>

<script>
import userData from '../data/users.json'
import companiesData from '../data/companies.json'

    export default {
        name: 'user-info',
        data: ()=>{
            return {

            }
        },
        props: {
            user: {
                type: Number,
                required : true},
        },
        computed:{
            showUserDetalies: function () {

                let findedUser = userData.find ((e)=>{
                    return e.id === this.user
                })

                let gender = findedUser.gender === 'Male' ? 'Mr ': 'Ms '
                let createString =gender +findedUser.first_name +' '+ findedUser.last_name

                let userCompany = companiesData.find ((e)=>{
                    return findedUser.company_id === e.id
                })

                if (userCompany === undefined) {
                    userCompany = {}
                }

                return {
                    fullName: createString,
                    birthday: findedUser.birthday,
                    avatar: findedUser.avatar,
                    company: userCompany
                }
            }
        },
        filters:{
            timeStampToFormatDate: (value)=>{
                // DD/MM/YYYY hh:mm:ss
                let date = new Date(value*1000);

                var dateN = "0" + date.getDate();
                var month = "0" + (date.getMonth()+1);
                var year = date.getFullYear()

                var formatedStamp = dateN.substr(-2)+'/'+month.substr(-2)+'/'+year

                return formatedStamp
            }
        }
    }

</script>