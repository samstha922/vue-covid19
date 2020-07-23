<template>
    <div id="announcements">
        <h1>Announcements </h1>
            <b-table responsive  :sort-by.sync="sortBy"
            :sort-desc.sync="sortDesc" sticky-header="stickyHeader" :items="items" :fields="fields" :class="rowClass">
                <template v-slot:cell(states)="data">
                    <router-link :to="`/states/${data.value}`">
                        {{data.value}}
                    </router-link>
                    <!-- <a :href="`#${data.value.toLowerCase()}`">{{ data.value }}</a> -->
                </template>
      </b-table>
    </div>
</template>
<script>
import axios from 'axios'   
	export default{
        name:'Announcements',
        data() {
            return{
                sortBy: 'states',
                sortDesc: false,
                fields: [{key:'states', label:'State', sortable: true},{key:'positives', label:'Positive', sortable: true}],     
                currency: '',
                items:[
                    {
                        // states:'',
                        // positives:''
                    }
                ]
                
            }
        },	
        mounted(){
            axios
            .get('https://covidtracking.com/api/states')
            .then((response) => { response.data.forEach(res => {
                                    this.items.push({states : res.state, positives: res.positive})
                                })
            })
            //checking the response for data which apparently isn't coming in 
            //.then(response => { this.responses = response.data}) 


            // axios
            // .get('https://query1.finance.yahoo.com/v8/finance/chart/TLS.AX?region=AU')
            // .then(console.log('saf'))

            // axios.get('https://query1.finance.yahoo.com/v8/finance/chart/TLS.AX?region=AU')
            // .then((response)=>{console.log(response.data);})	
        }	
	}
</script>