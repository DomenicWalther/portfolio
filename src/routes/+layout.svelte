<script>
  import Navigation from "$lib/Navigation.svelte";

  import "../app.postcss";

  window.onpointermove = (event) => {
    const { clientX, clientY } = event;

    blob.animate(
      {
        left: `${clientX}px`,
        top: `${clientY}px`,
      },
      { duration: 3000, fill: "forwards" }
    );
  };
</script>

<Navigation />

<slot />
