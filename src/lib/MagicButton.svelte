<script>
  import { scrollTo } from "svelte-scrolling";
</script>

<button
  class="magic-button text-gray900"
  use:scrollTo={{ ref: "work", offset: -200 }}
>
  <span>Check out my Work</span>
  <span>Check out my Work</span>
</button>

<style lang="scss">
  .magic-button {
    font-size: 1rem;
    font-weight: 600;

    display: grid;
    grid-template-areas: "center";
    place-items: center;

    padding: 1rem 1.5rem;
    border: none;
    border-radius: 40px;
    background-color: var(--yellow);
    position: relative;
    overflow: hidden;
    z-index: 1;

    transition: transform 0.5s;
    &:hover {
      transform: scale(0.97);
    }

    & > span {
      grid-area: center;
    }

    &:hover > span:first-child {
      transform: translatey(-100%);
      opacity: 0;

      transition: transform 0.5s, opacity 0.5s;
    }

    & > span:last-child {
      transform: translatey(100%);
      opacity: 0;
    }
    &:hover span:last-child {
      transform: translatey(0%);
      opacity: 1;

      transition: transform 0.5s, opacity 0.5s;
    }

    &::after {
      grid-area: center;
      content: "";
      width: 150%;
      aspect-ratio: 1 / 1;
      position: absolute;
      background-color: var(--yellow);
      border-radius: 100%;
      z-index: -1;

      box-shadow: 0 -50px 0 0 var(--purple), 0 -100px 0 0 var(--turquoise);
      transform: translatey(120%);

      transition: transform 0s;
    }

    &:hover::after {
      box-shadow: 0 0 0 0 var(--purple), 0 0 0 0 var(--turquoise);
      transform: translatey(0%);

      transition: transform 2s, box-shadow 3s;
    }
  }
</style>
