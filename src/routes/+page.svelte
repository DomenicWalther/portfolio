<script>
  import { onMount } from "svelte";

  const imageURL = "/images/background-image.jpg";

  const carouselText = [
    "I'm Domenic",
    "A Full-Stack Developer",
    "A Photographer",
    "A Inquisitive",
    "A Problem Solver",
  ];

  onMount(async () => {
    const eleRef = document.getElementById("feature-text");
    await carousel(carouselText, eleRef);
  });

  async function typeSentence(sentence, eleRef, delay = 100) {
    const letters = sentence.split("");
    let i = 0;
    while (i < letters.length) {
      await waitForMs(delay);
      eleRef.textContent += letters[i];
      i++;
    }
    return;
  }

  async function deleteSentence(eleRef) {
    const sentence = eleRef.textContent;
    const letters = sentence.split("");
    let i = 0;
    while (letters.length > 0) {
      await waitForMs(50);
      letters.pop();
      eleRef.textContent = letters.join("");
    }
  }

  async function carousel(carouselList, eleRef) {
    var i = 0;
    while (true) {
      await typeSentence(carouselList[i], eleRef);
      await waitForMs(1500);
      await deleteSentence(eleRef);
      await waitForMs(500);
      i++;
      if (i >= carouselList.length) {
        i = 0;
      }
    }
  }

  function waitForMs(ms) {
    return new Promise((resolve) => setTimeout(resolve, ms));
  }
</script>

<div class="z-10 flex min-h-screen flex-col items-center justify-center">
  <nav class="z-20 absolute top-10 left-40 text-shadow">
    <ul class="flex justify-center">
      <li class="mr-6">
        <a href="#" class="text-white hover:text-purple-300 transition-colors"
          >00 Home</a
        >
      </li>
      <li class="mr-6">
        <a href="#" class="text-white hover:text-purple-300 transition-colors"
          >01 About</a
        >
      </li>
      <li class="mr-6">
        <a href="#" class="text-white hover:text-purple-300 transition-colors"
          >02 Projects</a
        >
      </li>
    </ul>
  </nav>
  <img src={imageURL} alt="" class="absolute h-full w-full object-cover" />
  <div class="screen-overlay" />
  <div
    class="text-white text-7xl z-10 absolute left-40 top-80 typing-container text-shadow"
  >
    <span id="sentence" class="sentence">Hello,</span><br />
    <span id="feature-text" />
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
    height: 3.75rem;
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
</style>
