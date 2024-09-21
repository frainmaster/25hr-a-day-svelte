<script>
  import Timer25 from './lib/Timer25.svelte'
  import Timer24 from './lib/Timer24.svelte'
  import Converter from './lib/Converter.svelte'
  import Desc from './lib/Description.svelte'
</script>

<main>
  <h1>25-Hour Day</h1>
  <h4>When 24 hour is never enough</h4>
  <div class="vertical-gap">
    <h3>25-Hour Format</h3>
    <Timer25 />
    <hr>
    <Timer24 />
    <h3>24-Hour Format</h3>
  </div>
  <div class="vertical-gap">
    <Converter />
  </div>
  <div class="vertical-gap">
    <Desc />
  </div>
  <h5>© 2024 By <a href="https://frainmaster.com/">frainmaster</a></h5>
</main>

<style>
  .vertical-gap {
    padding: 25px 0px;
  }
  main {
    max-width: 720px;
  }
</style>