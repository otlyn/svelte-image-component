<script>
  // export let landscape = false;
  // export let portrait = false;
  // export let square = false;

  export let src;
  export let size;
  export let sizes;
  export let className;
  export let alt = src.split(".").shift();

  // "image.jpg" => ["image", "jpg"]
  const nameSplit = src.split(".");

  // ["image", "jpg"] => "image"
  const fileName = nameSplit.shift();
  // ["jpg"] => "jpg"
  const fileType = nameSplit.pop();

  // Path to image directory
  const path = "images";

  // Sizes based on px
  const xs = `${path}/${fileName}@xs.${fileType} 150w`;
  const sm = `${path}/${fileName}@sm.${fileType} 300w`;
  const md = `${path}/${fileName}@md.${fileType} 600w`;
  const lg = `${path}/${fileName}@lg.${fileType} 1200w`;
  const xl = `${path}/${fileName}@xl.${fileType} 2400w`;
</script>

{#if size == 'sm'}
  <img src={sm} srcset="{xs}, {sm}, {md}" {sizes} {alt} class={className} />

{:else if size == 'md'}
  <img src={md} srcset="{sm}, {md}, {lg}" {sizes} {alt} class={className} />

{:else if size == 'lg'}
  <img src={lg} srcset="{md}, {lg}, {xl}" {sizes} {alt} class={className} />

{:else}
  <img
    src={md}
    srcset="{xs}, {sm}, {md}, {lg}, {xl}"
    {sizes}
    {alt}
    class={className} />
{/if}

<style>
  /* Responsive scaling */
  img {
    width: 100%;
    height: auto;
  }
</style>
