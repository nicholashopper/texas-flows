<template>
  <nuxt-link
              tag="span"
              :to="getRoute()"
              id="RiverButton"
              class="box"
              v-if="river.name">
    <div class="chart">
      <div class="info">
        <b>
          <h1>{{ river.rating }}</h1>
          <h5>{{ river.name }}</h5>
        </b>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
var _ = require('lodash');

export default {
  name: "RiverButton",
  props: ['river'],
  methods: {
    getRoute() {
      return '/rivers/' + _.kebabCase(this.river.name);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
span.box {
  display: inline-block;
  width: 160px;
  height: 160px;
  padding: 16px;   
  margin: 16px;
  background-color: white; 
  box-shadow: 0 0 10px gray;
  text-align: center;
  overflow: hidden;
}

div.chart {
  width: 128px;
  height: 128px;
	padding: 8px;
	text-align: center;
  display: inline-block;
  background-color: #888;
  color: white; 
}

div.info {
  margin: auto;
  padding-top: 24px;
}

span.box:hover {
  background-color: #fafafa;
  box-shadow: 0 0 8px gray;
}
</style>