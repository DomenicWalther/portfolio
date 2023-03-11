<script>
  import { onMount } from "svelte";
  import HackerText from "$lib/utils/HackerText";
  import carousel from "$lib/utils/Typewriter";

  const imageURL = "/images/background-image.jpg";

  const carouselText = [
    "A Full-Stack Developer",
    "A Photographer",
    "A Inquisitive",
    "A Problem Solver",
  ];

  onMount(async () => {
    const eleRef = document.getElementById("feature-text");
    await carousel(carouselText, eleRef);
  });
</script>

<div class="z-10 flex min-h-screen flex-col items-center justify-center">
  <img src={imageURL} alt="" class="absolute h-full w-full object-cover" />
  <div class="screen-overlay" />
  <div
    class="text-white font-bold text-4xl z-10 md:text-3xl leading-none absolute left-20 lg:left-40 top-80 typing-container"
  >
    <span
      id="sentence"
      class="sentence interactable text-xl"
      data-value="Hello,"
      on:mouseover={(e) => HackerText(e)}>Hi, I am</span
    ><br />
    <p>
      <span>Domenic Walther.</span><span class="wave">👋</span>
    </p>
    <span id="feature-text" class="text-xl" />
    <span class="input-cursor" />
  </div>
</div>

<style lang="scss">
  :root {
    --blue-rgb: 112 41 99;
    --primary-rgb: var(--blue-rgb);
  }

  .text-shadow {
    text-shadow: 0px 0px 0.5rem white;
  }

  .wave {
    animation-name: wave-animation;
    animation-duration: 2.5s;
    animation-iteration-count: infinite;
    transform-origin: 70% 70%;
    display: inline-block;
  }

  .screen-overlay {
    background: linear-gradient(
      rgb(var(--primary-rgb) / 0.15),
      rgb(var(--primary-rgb) / 0.15) 3px,
      transparent 3px,
      transparent 9px
    );
    background-size: 100% 9px;
    height: 100%;
    width: 100%;
    animation: pan-overlay 20s infinite linear;
    position: absolute;
    left: 0px;
    top: 0px;
    z-index: 2;
  }
  .input-cursor {
    display: inline-block;
    width: 2px;
    height: 1.25rem;
    background-color: white;
    margin-left: 8px;
    animation: blink 0.6s linear infinite alternate;
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

  @keyframes pan-overlay {
    from {
      background-position: 0% 0%;
    }

    to {
      background-position: 0% -100%;
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
