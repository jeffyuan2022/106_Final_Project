<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import Map from "./Map.svelte";

  let count, index, offset, progress;
</script>
<Scroller
  top={0.0}
  bottom={1}
  threshold={0.5}
  bind:count
  bind:index
  bind:offset
  bind:progress
>
  <div class="background" slot="background">
    <Map {index} />
    <div class="progress-bars">
      <p>current section: <strong>{index + 1}/{count}</strong></p>
      <progress value={count ? (index + 1) / count : 0} />

      <p>offset in current section</p>
      <progress value={offset || 0} />

      <p>total progress</p>
      <progress value={progress || 0} />
    </div>
  </div>

  <div class="foreground" slot="foreground">
    <section>This is the first section.</section>
    <section>This is the second section.</section>
    <section>This is the third section.</section>
  </div>

</Scroller>
<style>
  /* .background {
    width: 100%;
    height: 100vh;
    position: relative;
    outline: green solid 3px;
  } */

  /* .foreground {
    width: 50%;
    margin: 0 auto;
    height: auto;
    position: relative;
    outline: red solid 3px;
  } */

  .progress-bars {
    position: absolute;
    background: rgba(170, 51, 120, 0.2) /*  40% opaque */;
    visibility: hidden;
  }

  section {
    height: 80vh;
    background-color: rgba(255, 255, 255, 0.2); /* 20% opaque */
    /* color: white; */
    outline: rgb(255, 255, 255) solid 3px;
    text-align: center;
    max-width: 750px; /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
  }
</style>
