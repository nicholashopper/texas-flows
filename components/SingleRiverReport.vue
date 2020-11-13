<template>
  <div id="SingleRiverReport">
    <h1> {{ riverName }} </h1>
    <div v-if="isLoaded">
      {{ river }}
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleRiverReport",
  props: {
    riverName: String
  },
  data() {
    return {
      isLoaded: false,
      river: new Object()
    }
  },
  async mounted() {
    const rivers = await import("../rivers.json");
    this.river = _.find(rivers, { 'name': this.riverName });


    console.log(this.river);
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