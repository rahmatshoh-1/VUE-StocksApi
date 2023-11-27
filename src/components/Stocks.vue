<template>
    <div class="grid md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 mx-3 gap-4">
        <div v-for="value in stock" :key="value.stock" class="flex justify-between items-center border border-gray-400 rounded-lg p-4">
            <div class="inline-flex">
                <img class="h-11 mr-8 " :src="value.image" :alt="value.companyName">
              <div>
                <h3>{{value.companyName}}</h3>
                <span>{{value.symbol}}</span>
              </div>
            </div>
            <span>{{value.price}}$</span>
        </div>
    </div>
    <h3 class="text-3xl font-bold mt-16 mx-3 mb-5">Get Stocks Info</h3>
    <select v-model="selected" class="p-3 bg-gray-200 rounded-lg select mx-3">
        <option value="" disabled>Select Company</option>
        <option :value="value.description" class="px-2" v-for="value in stock" :key="stock" >{{value.companyName}}</option>
    </select>
    <div class="my-4 mx-3">
        {{selected}}
    </div>
</template>

<script>
    import axios from 'axios'

    export default{
        name:'Stocks',
        data(){
            return{
                stock:[],
                errors:[],
                selected:''
            }
        },
        created(){
                axios.get('https://financialmodelingprep.com/api/v3/profile/AAPL,TSLA,AMD,INTC,MDB,SPCE,V,DAL,DOCU,OKTA,GDDY,AMZN,TRIP,NVDA?apikey=1adfe4e86d158280b7facb0a441aff09').
                then(response=>{
                    this.stock =response.data
                    console.log(response)
                })
                .catch(e=>{
                    this.errors.push(e)
                })
            }
    }
</script>