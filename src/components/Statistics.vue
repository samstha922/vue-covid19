<template>
    <div id="stats">
        <h1>Statistics </h1>
        {{states}} 
        {{positives}}
        <canvas id="planet-chart"></canvas>
    </div>
</template>
<script>
import { Line } from 'vue-chartjs'
import axios from 'axios'
	export default {
        extends: Line,
        name:'Statistics',
        props: ['chartdata', 'options'],
        data() {
            return{
                    states : [],
                    positives : []

            }
        },	
        mounted () {
           // console.log('canvas'+this.chartdata)
            axios
            .get('https://covidtracking.com/api/states')
            .then((response) => { response.data.forEach(eachState => {
                                    this.states.push(eachState.states) 
                                    this.positives.push(eachState.positive) 
                                })
                })
            // .then((jsonData) =>{
            //     jsonData.forEach(eachState => {
            //         this.states.push(eachState.state)  
            //     })
            // })
        }
        // methods:{
        //     createChart(chartId, chartData) {
        //         const ctx = document.getElementById(chartId);
        //         const myChart = new Chart(ctx, {
        //             type: chartData.type,
        //             data: chartData.states,
        //             options: chartData.options
        //         })
        //     }
        // }
    }
</script>