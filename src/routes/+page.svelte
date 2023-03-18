<script>
  import { onMount } from "svelte";
  import carousel from "$lib/utils/Typewriter";
  import MagicButton from "$lib/MagicButton.svelte";
  import { scrollRef, scrollTop } from "svelte-scrolling";

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
  class="text-white text-xl md:text-4xl max-w-xs md:max-w-2xl lg:max-w-4xl relative z-50 mx-auto my-0 flex justify-center content-start flex-col h-screen min-h-screen"
>
  <h2 class="text-green text-xl">Hi, my name is</h2>
  <h1 class="pt-4 md:pt-14 text-gray-200 big-heading">
    Domenic Walther. <span class="wave text-xl md:text-7xl">👋</span>
  </h1>
  <span class="text-2xl big-heading py-5 font-bold text-gray-200"
    >A <span id="feature-text" />
    <div class="input-cursor" /></span
  >
  <p class="text-lg text-gray-400">
    As a Frontend Developer and Python Programmer, I'm always on the lookout for
    fresh opportunities to hone my craft and tackle new challenges. My unbridled
    passion for technology drives me to stay abreast of the latest industry
    trends and developments.
  </p>
  <div class="pt-10">
    <MagicButton />
  </div>
</section>
<section
  class="max-w-4xl relative top-0 z-50 mx-auto my-0 flex content-start flex-col h-screen"
  id="work"
  use:scrollRef={"work"}
>
  <div class="text-4xl">About Me</div>
  <div>
    I'm 23 years old and based near Würzburg, Germany. My passion for technology
    and its application motivates me to explore new possibilities and develop
    innovative solutions.
  </div>
  <div>
    As an enthusiastic web developer with a strong interest in technology and
    its application, my journey in the industry began in 2014 when I completed
    an internship at an advertising agency. Since then, I have continously
    improved my skills by occasionally developing small projects, such as a
    mini-spotlight clone for Windows.
  </div>
  <div>
    Currently, I am working on creating Software for my current company,
    including automating the process of storing images and a local task list
    that the entire team can access on the network to organize tasks more
    efficiently. This has further improved my skills in front-end and back-end
    development.
  </div>
  <div>
    I love to learn new things and constantly expand my skills. It's important
    for me to feel like I've progressed every day. As a motivated and dedicated
    developer, I'm ready to apply my knowledge and skills to new projects and
    challenges.
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
    position: fixed;
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
    position: fixed;
    z-index: 1;
    backdrop-filter: blur(12vmax);
  }

  .big-heading {
    font-size: clamp(20px, 8vw, 80px);
    line-height: clamp(40px, 8vw, 80px);
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
    height: clamp(40px, 8vw, 80px);
    background-color: white;
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
