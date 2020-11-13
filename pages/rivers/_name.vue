<template>
  <div class="container">
    <div class="river-page">
      <SingleRiverReport
        v-bind:riverName="getRiverName()"
      ></SingleRiverReport>
    </div>
  </div>
</template>

<script>
var _ = require('lodash');
export default {
  // $nuxt.$route.path
  methods: {
    undoKebabCase(kebabCase) {
      let regularCase = kebabCase;
      regularCase = _.replace(regularCase, '-', ' ')

      let wordsInName = _.words(regularCase);
      wordsInName = _.map(wordsInName, word => _.upperFirst(word));
      regularCase = _.join(wordsInName, ' ');

      return regularCase;
    },
    getRiverName() {
      let path = this.$nuxt.$route.path.replace('/rivers/', '');

      return this.undoKebabCase(path);
    }
  }
}

// export default {
//   name: "RiverButton",
//   props: ['river'],
//   methods: {
//     getRoute() {
//       return '/rivers/' + _.kebabCase(this.river.name);
//     }
//   }
// };
</script>

<style>
.river-page {
  background-color: white;
  padding-top: 32px;
  padding-right: 32px;
  padding-bottom: 16px;
  padding-left: 32px;
}

</style>
