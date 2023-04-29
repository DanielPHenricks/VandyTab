<!-- This is the main page for the Vandy Tab. -->
<script>
  import Clock from "./lib/Clock.svelte";
  import ButtonGroup from "./lib/ButtonGroup.svelte";
  import Greeting from "./lib/Greeting.svelte";
  import Tables from "./lib/Tables.svelte";
  import Setup from "./lib/Setup.svelte";
  const numImages = 7;
  let image = Math.ceil(Math.random() * numImages);

  // Set up preferences
  let showSetup = false;
  let firstVisit = localStorage.getItem("visited");
  if (!firstVisit) {
    localStorage.setItem("visited", "true");
    showSetup = true;
  }

  // @ts-ignore
  document.body.background = `../images/vandy${image}.jpg`;
</script>

<html lang="en-us">
  <main>
    {#if !showSetup}
      <Clock />
      <Greeting />
      <ButtonGroup />
      <Tables />
    {/if}
    {#if showSetup}
      <div class="container">
        <Setup />
      </div>
    {/if}
  </main>
</html>

<style>
  .container::before {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba(255, 255, 255, 0.4);
    z-index: -1;
  }
</style>
