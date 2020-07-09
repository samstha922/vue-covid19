<template>
    <div id="stats">
        <h1>Statistics </h1>
        <canvas ref="canvas" width="900" height="400"></canvas>
    </div>
</template>
<script>
import { Line } from 'vue-chartjs'
import axios from 'axios'
	export default {
        extends: Line,
        name:'Statistics',
        data() {
            return{
                    states : [],
                    positives : [],
                    flag: false

            }
        },
        mounted () {
            axios
            .get('https://covidtracking.com/api/states')
            .then((response) => { response.data.forEach(eachState => {
                                    this.states.push(eachState.state) 
                                    this.positives.push(eachState.positive) 
                                })
                this.renderChart({
                labels: this.states,
                datasets: [
                    {
                    label: 'States',
                    backgroundColor: '#f87979',
                    data: this.positives
                    }
                ]
                }, {responsive: true, maintainAspectRatio: true})
            })
        } 
    }
</script>