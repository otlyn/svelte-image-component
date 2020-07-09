<script>
  export let src;
  export let alt = src;
  export let landscape = false;
  export let portrait = false;
  export let square = false;
</script>

<!-- Change image directory to correct path -->
<!-- Image sizing: 600px = sm, 1200px = md, 2400px = lg -->

{#if landscape}
  <img
    src="http://via.placeholder.com/1200x900"
    srcset="http://via.placeholder.com/600x450 600w,
    http://via.placeholder.com/1200x900 1200w,
    http://via.placeholder.com/2400x1800 2400w"
    {alt} />

{:else if portrait}
  <img
    src="http://via.placeholder.com/900x1200"
    srcset="http://via.placeholder.com/450x600 600w,
    http://via.placeholder.com/900x1200 1200w,
    http://via.placeholder.com/1800x2400 2400w"
    {alt} />

{:else if square}
  <img
    src="http://via.placeholder.com/1200"
    srcset="http://via.placeholder.com/600 600w, http://via.placeholder.com/1200
    1200w, http://via.placeholder.com/2400 2400w"
    {alt} />
{:else}
  <img
    src="images/{src}-md.jpg"
    srcset="images/{src}-sm.jpg 600w, images/{src}-md.jpg 1200w, images/{src}-lg.jpg
    2400w"
    {alt} />
{/if}

<style>
  /* Responsive scaling */
  img {
    width: 100%;
    height: auto;
  }
</style>
