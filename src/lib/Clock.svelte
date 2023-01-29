<!-- This updates a clock using the "$" operator. -->
<script>
  import { onMount } from "svelte";
  let time = new Date();
  $: hour = time.getHours() % 12 != 0 ? time.getHours() % 12 : 12;
  $: minutes = time.getMinutes();
  $: seconds = time.getSeconds();
  $: if (minutes < 10) {
    minutes = "0" + minutes;
  }
  $: if (seconds < 10) {
    seconds = "0" + seconds;
  }
  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000);

    return () => {
      clearInterval(interval);
    };
  });
</script>

<div class="container mt-4">
  <div class="row">
    <div class="col-md-12 text-center">
      <h1 id="clock">{hour}:{minutes}:{seconds}</h1>
    </div>
  </div>
</div>
