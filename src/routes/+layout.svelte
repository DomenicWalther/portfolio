<script>
  import Navigation from "$lib/Navigation.svelte";
  import { onMount } from "svelte";
  import "../app.postcss";

  const animateTrailer = (e, interacting) => {
    const x = e.clientX - trailer.offsetWidth / 2;
    const y = e.clientY - trailer.offsetHeight / 2;

    const keyframes = {
      transform: `translate(${x}px, ${y}px) scale(${interacting ? 2 : 1})`,
    };

    trailer?.animate(keyframes, {
      duration: 800,
      fill: "forwards",
    });
  };
  window.onmousemove = (e) => {
    const interactable = e.target.closest(".interactable"),
      interacting = interactable !== null;

    const icon = document.getElementById("trailer-icon");

    animateTrailer(e, interacting);

    trailer.dataset.type = interacting ? interactable.dataset.type : "";

    if (interacting) {
      icon.className = getTrailerClass(interactable.dataset.type);
    }
  };

  onMount(async () => {
    const trailer = document.getElementById("trailer");
  });
</script>

<Navigation />
<div id="trailer">
  <i id="trailer-icon" />
</div>
<slot />

<style lang="postcss">
  #trailer {
    height: 20px;
    width: 20px;
    background-color: white;
    border-radius: 20px;
    position: fixed;
    left: 0px;
    top: 0px;
    z-index: 10000;
    pointer-events: none;
  }
</style>
