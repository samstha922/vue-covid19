<template>
    <div id="announcements">
        <p>Announcements</p>
    </div>
</template>
<script>
import axios from 'axios'
	export default{
        name:'Announcements',
        data() {
            return{
            }
        },	
        mounted(){
            axios
            .get('https://covidtracking.com/api/states')
            .then((response) => { response.data.forEach(eachState => {
                                    this.states.push(eachState.state) 
                                    this.positives.push(eachState.positive) 
                                })
            })

        }		
		
	}
</script>