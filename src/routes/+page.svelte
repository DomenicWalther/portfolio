<script>
  import { onMount } from "svelte";
  import HackerText from "$lib/utils/HackerText";
  import carousel from "$lib/utils/Typewriter";
  import MagicButton from "$lib/MagicButton.svelte";

  const carouselText = [
    "Full-Stack Developer",
    "Photographer",
    "Inquisitive",
    "Problem Solver",
  ];

  onMount(async () => {
    const eleRef = document.getElementById("feature-text");
    await carousel(carouselText, eleRef);
  });
</script>

<div id="blur" />
<div id="blob" />
<section
  class="text-white text-4xl max-w-4xl relative z-50 mx-auto my-0 flex justify-center content-start flex-col h-screen"
>
  <h2 class="text-green text-xl">Hi, my name is</h2>
  <h1 class="pt-5 text-gray-200">
    Domenic Walther. <span class="wave">👋</span>
  </h1>
  <span
    >A <span id="feature-text" />
    <div class="input-cursor" /></span
  >
  <p class="text-lg text-gray-400">Some random fun text.</p>
  <div class="pt-10">
    <MagicButton />
  </div>
</section>

<style lang="scss">
  :root {
    --blue-rgb: 112 41 99;
    --primary-rgb: var(--blue-rgb);
    --purple: rgb(163, 116, 255);
    --turquoise: rgb(23, 241, 209);
    --yellow: rgba(255, 208, 116);
  }
  #blob {
    background-color: white;
    height: 34vmax;
    aspect-ratio: 1;
    position: absolute;
    left: 50%;
    top: 50%;
    translate: -50% -50%;
    border-radius: 50%;
    background: linear-gradient(to right, aquamarine, mediumpurple);
    animation: rotate 20s infinite;
    opacity: 0.8;
  }

  #blur {
    height: 100%;
    width: 100%;
    position: absolute;
    z-index: 1;
    backdrop-filter: blur(12vmax);
  }

  section {
    z-index: 10;
  }

  .wave {
    animation-name: wave-animation;
    animation-duration: 2.5s;
    animation-iteration-count: infinite;
    transform-origin: 70% 70%;
    display: inline-block;
  }

  .input-cursor {
    display: inline-block;
    width: 2px;
    height: 2rem;
    background-color: white;
    margin-left: 8px;
    transform: translatey(3px);
    animation: blink 0.6s linear infinite alternate;
  }

  @keyframes rotate {
    from {
      rotate: 0deg;
    }

    50% {
      scale: 1 1.5;
    }
    to {
      rotate: 360deg;
    }
  }

  @keyframes blink {
    0% {
      opacity: 1;
    }
    40% {
      opacity: 1;
    }
    60% {
      opacity: 0;
    }
    100% {
      opacity: 0;
    }
  }

  @keyframes wave-animation {
    0% {
      transform: rotate(0deg);
    }
    10% {
      transform: rotate(14deg);
    }
    20% {
      transform: rotate(-8deg);
    }
    30% {
      transform: rotate(14deg);
    }
    40% {
      transform: rotate(-4deg);
    }
    50% {
      transform: rotate(10deg);
    }
    60% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(0deg);
    }
  }
</style>
