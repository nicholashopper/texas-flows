<template>
  <div class="container">
    <div>
      <div style="margin: 128px"/>
      <TotalRiverReport />
      <p>
        This site is under construction. Stay tuned. 
      </p>

      <div class="links">
        <a
          href="https://nicholas.works/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Built by Hopper
        </a>
        <a
          href="https://github.com/nicholashopper/texas-flows"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
