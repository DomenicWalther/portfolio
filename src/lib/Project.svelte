<script>
  import { goto } from "$app/navigation";
  import { onMount } from "svelte";

  onMount(async () => {
    document.getElementById("cards").onmousemove = (e) => {
      for (const card of document.getElementsByClassName("card")) {
        const rect = card.getBoundingClientRect(),
          x = e.clientX - rect.left,
          y = e.clientY - rect.top;
        card.style.setProperty("--mouse-x", `${x}px`);
        card.style.setProperty("--mouse-y", `${y}px`);
      }
    };
  });

  const projects = [
    {
      name: "StudioMate",
      description:
        "A Studio Management App for Photographers to help their business & workflow.",
      imageURL: "/images/studiomate-project.jpg",
    },
    {
      name: "Schwabify",
      description:
        "Internally developed tool to help save time when pulling Images from SD-Cards into a Client-Specific Folder.",
    },
  ];
</script>

<div id="cards">
  {#each projects as project}
    <div class="card cursor-pointer">
      <div class="card-content">
        <img
          src={project.imageURL}
          alt="Studiomate UI Mockup"
          class="items-center flex object-contain w-11/12 mx-auto pt-3 justify-center  rounded-xl"
        />
        <div
          class="card-info-wrapper items-center flex flex-grow justify-start py-7 px-5"
        >
          <div class="card-info text-white flex items-start gap-3 z-50">
            <h3 class="font-bold">{project.name}</h3>
            <h4 class="text-base font-light">{project.description}</h4>
            <h5
              class="text-xs whitespace-nowrap absolute bottom-1 right-5 text-gray-300"
            >
              Click for more Information
            </h5>
          </div>
        </div>
      </div>
    </div>
  {/each}
</div>

<style lang="postcss">
  :root {
    --card-color: rgb(23, 23, 23);
  }
  #cards {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    width: calc(100% - 20px);
  }
  #cards:hover > .card::after {
    opacity: 1;
  }

  .card {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
    display: flex;
    height: 350px;
    flex-direction: column;
    position: relative;
    width: 450px;
  }

  .card:hover::before {
    opacity: 1;
  }

  .card::before,
  .card::after {
    border-radius: inherit;
    content: "";
    height: 100%;
    left: 0px;
    opacity: 0;
    position: absolute;
    top: 0px;
    transition: opacity 500ms;
    width: 100%;
  }

  .card::before {
    background: radial-gradient(
      800px circle at var(--mouse-x) var(--mouse-y),
      rgba(255, 255, 255, 0.06),
      transparent 40%
    );
    z-index: 3;
  }

  .card::after {
    background: radial-gradient(
      600px circle at var(--mouse-x) var(--mouse-y),
      rgba(255, 255, 255, 0.4),
      transparent 40%
    );
    z-index: 1;
  }

  .card > .card-content {
    background-color: var(--card-color);
    border-radius: inherit;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    inset: 1px;
    position: absolute;
    z-index: 2;
  }
</style>
