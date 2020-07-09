<script>
  import Image from "./Image.svelte";
</script>

<!-- The "src" path is relative to public/images/ -->
<Image src="image" alt="Description" />

<!-- Placeholder images -->
<Image landscape={true} />

<Image portrait={true} />

<Image square={true} />
