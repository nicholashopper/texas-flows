<template>
  <div id="SingleReport">
    <div>
      <h1>{{ river.name }} </h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleRiverReport",
  props: ['river']
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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