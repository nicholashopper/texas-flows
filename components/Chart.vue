<template>
  <div class="small">
    <line-chart :chart-data="datacollection"
                v-bind:options="options"></line-chart>
    <button @click="fillData()">Randomize</button>
  </div>
</template>

<script>
  import LineChart from './LineChart.js'

  export default {
    components: {
      LineChart
    },
    data () {
      return {
        datacollection: null,
        options: null
      }
    },
    mounted () {
      this.fillData()
      this.options = {
        scales: {
          yAxes: [{
            id: 'A',
            type: 'linear',
            position: 'left',
          }]
        }
      }
    },
    methods: {
      fillData () {
        var canvas = document.getElementById("line-chart");
        var ctx = canvas.getContext("2d");
        var gradient = ctx.createLinearGradient(0, 0, 0, 400);
        gradient.addColorStop(0, '#0A7ACF');
        gradient.addColorStop(0.25, 'rgba(4, 179, 243, .90)');   
        gradient.addColorStop(1, 'rgba(164, 228, 252, .5)');

        this.datacollection = {
          labels: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
          datasets: [
            {
              label: 'River Flow: Cubic Feet Per Second',
              yAxisID: 'A',
              backgroundColor: gradient,
              data: [this.getRandomInt(), this.getRandomInt(), this.getRandomInt(),this.getRandomInt(), this.getRandomInt(), this.getRandomInt(),this.getRandomInt()]
            }
          ]
        }
      },
      getRandomInt () {
        return (Math.floor(Math.random() * (50 - 5 + 1)) + 5)
      }
    }
  }
</script>

<style>
  .small {
    max-width: 600px;
    margin:  150px auto;
  }
</style>