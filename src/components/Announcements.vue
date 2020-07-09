<template>
    <div id="announcements">
        <p>Announcements</p>
         <b-table responsive  :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc" sticky-header="stickyHeader" :items="items" :fields="fields" :class="rowClass"></b-table>
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
                fields: [{key:'states', sortable: true},{key:'positives', sortable: true}],     
               

                items:[
                    {
                        states:'',
                        positives:''
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
        },
        methods:{
            rowClass(item, type){
                if (!item || type !== 'row') return
                if (item.positives == '0') return 'table-success'
            }

        }		
		
	}
</script>