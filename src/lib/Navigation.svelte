<script lang="ts">
  import { scrollTo } from "svelte-scrolling";
  let y: number;

  let isNavbarShowing = false;

  const toggleNavbar = () => {
    isNavbarShowing = !isNavbarShowing;
  };
</script>

<nav
  class={isNavbarShowing || y > 100
    ? "default-nav bg-mainbackground"
    : "default-nav"}
>
  <div>
    <h2 class="text-white font-bold text-xl">domenic.dev</h2>
  </div>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    id="menu-button"
    class="h-6 w-6 cursor-pointer md:hidden block"
    fill="none"
    viewBox="0 0 24 24"
    stroke="white"
    on:click={toggleNavbar}
  >
    <path
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M4 6h16M4 12h16M4 18h16"
    />
  </svg>
  <div
    class={isNavbarShowing ? "navbar-class" : "navbar-class hidden "}
    id="menu"
  >
    <ul class="pt-4 text-base text-gray-700 md:flex md:justify-between md:pt-0">
      <li class="mr-6">
        <a
          href="/"
          on:click={toggleNavbar}
          class="text-white hover:text-purple-300 transition-colors md:p-4 py-2 block"
          ><span class="text-green">01.</span> Home</a
        >
      </li>
      <li class="mr-6">
        <a
          href=""
          use:scrollTo={{ ref: "work", offset: -200 }}
          on:click={toggleNavbar}
          class="text-white hover:text-purple-300 transition-colors md:p-4 py-2 block"
          ><span class="text-green">02.</span> Work</a
        >
      </li>
      <li class="mr-6">
        <a
          href="#"
          on:click={toggleNavbar}
          class="text-white hover:text-purple-300 transition-colors md:p-4 py-2 block"
          ><span class="text-green">03.</span> About Me</a
        >
      </li>
      <li class="mr-6">
        <a
          href="#"
          on:click={toggleNavbar}
          class="text-white hover:text-purple-300 transition-colors md:p-4 py-2 block"
          ><span class="text-green">04.</span> Contact</a
        >
      </li>
    </ul>
  </div>
</nav>

<svelte:window bind:scrollY={y} />

<style>
  ul > li {
    opacity: 1;
    transition: opacity 0.5s;
  }
  ul:hover > li {
    opacity: 0.25;
    transition: opacity 0.5s;
  }
  ul > li:hover {
    opacity: 1;
    transition: opacity 0.5s;
  }

  .default-nav {
    @apply z-20 fixed flex flex-wrap items-center justify-between w-full py-6 md:py-4 px-4 text-lg;
    transition: background-color 0.45s, box-shadow 0.45s;
  }

  .navbar-class {
    @apply w-full md:flex md:items-center md:w-auto;
  }
</style>
