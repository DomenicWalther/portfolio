<nav
  class="z-20 fixed px-10 h-24 items-center flex top-0 py-0 justify-between w-full"
>
  <h2 class="text-white font-bold text-xl">domenic.dev</h2>
  <ul class="flex justify-center interactable">
    <li class="mr-6">
      <a href="/" class="text-white hover:text-purple-300 transition-colors"
        ><span class="text-green">01.</span> Home</a
      >
    </li>
    <li class="mr-6">
      <a href="/work" class="text-white hover:text-purple-300 transition-colors"
        ><span class="text-green">02.</span> Work</a
      >
    </li>
    <li class="mr-6">
      <a href="#" class="text-white hover:text-purple-300 transition-colors"
        ><span class="text-green">03.</span> About Me</a
      >
    </li>
    <li class="mr-6">
      <a href="#" class="text-white hover:text-purple-300 transition-colors"
        ><span class="text-green">04.</span> Contact</a
      >
    </li>
  </ul>
</nav>

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
</style>
