<!-- This is the main page for the Vandy Tab. -->
<script>
  import Clock from "./lib/Clock.svelte";
  import ButtonGroup from "./lib/ButtonGroup.svelte";
  import Greeting from "./lib/Greeting.svelte";
  import Tables from "./lib/Tables.svelte";
  import Setup from "./lib/Setup.svelte";
  const numImages = 3;
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
  <Clock />
  {#if !showSetup}
    <Greeting />
    <ButtonGroup />
    <Tables />
  {/if}
  {#if showSetup}
    <Setup />
  {/if}
</html>
