<template>
  <div class="small">
    <div v-if="isLoaded">
      <line-chart :chart-data="datacollection"
                  v-bind:options="options"></line-chart>
    </div>
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
        isLoaded: false,
        datacollection: null,
        options: null
      }
    },
    async mounted () {
      this.fillData();
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
      async fillData () {
        const river  = await import("../river.json");

        this.datacollection = {
          labels: this.renderLabels(river),
          datasets: [
            {
              label: river.metric,
              yAxisID: 'A', // Makes data set unique
              backgroundColor: 'rgba(75,192,192,0.4)', //this.getGradient(),
              data: river.timeSeries
            }
          ]
        }
        this.isLoaded = true;
      },
      renderLabels(river) {
        let days = []
        days.push(river.startDate);

           for(var i = 0; i < river.timeSeries.length-60; i++) {
              days.push('');
           }
        // Access river.timeSeries.length => 60
        days.push(river.endDate);
        return days;
      
      },
      getGradient() {
        var canvas = document.getElementById("line-chart");
        var ctx = canvas.getContext("2d");
        var gradient = ctx.createLinearGradient(0, 0, 0, 400);
        gradient.addColorStop(0, '#0A7ACF');
        gradient.addColorStop(0.25, 'rgba(4, 179, 243, .90)');   
        gradient.addColorStop(1, 'rgba(164, 228, 252, .5)');
        return gradient;
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