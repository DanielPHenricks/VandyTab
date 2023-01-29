<!-- This is the main page for the Vandy Tab. -->
<script>
  import Clock from "./lib/Clock.svelte";
  import ButtonGroup from "./lib/ButtonGroup.svelte";
  import Greeting from "./lib/Greeting.svelte";
  import DiningHallTable from "./lib/DiningHallTable.svelte";
  import Tables from "./lib/Tables.svelte";
  const numImages = 3;
  let image = Math.ceil(Math.random() * numImages);
  document.body.background = `../images/vandy${image}.jpg`;
</script>

<html lang="en-us">
  <Clock />
  <Greeting />
  <ButtonGroup />
  <Tables />
</html>
