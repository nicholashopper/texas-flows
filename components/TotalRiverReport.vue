<template>
  <div id="TotalRiverReport">
    <div v-if="isLoaded">
      <RiverButton
        v-for="river in rivers"
        v-bind:key="river.name"
        v-bind:river="river"
      ></RiverButton>
    </div>
  </div>
</template>

<script>
export default {
  name: "TotalRiverReport",
  // props: {
    
  // },
  data() {
    return {
      isLoaded: false,
      rivers: []
    }
  },
  async mounted() {
    const rivers = await import("../rivers.json");
    this.rivers = rivers;
    console.log(this.rivers);
    this.isLoaded = true;
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
div {
  overflow: hidden;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>