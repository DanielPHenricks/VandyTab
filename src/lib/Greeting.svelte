<!-- 
  This component is a greeting displayed below the clock. 
  Last changed: 4/17/23
-->

<script>
  // @ts-nocheck
  let time = new Date();
  let hours = time.getHours();
  let name = localStorage.name;
  let phrase;
  const setPhrase = () => {
    phrase = "Good ";
    if (hours >= 6 && hours <= 12) {
      phrase += "morning, ";
    } else if (hours <= 18) {
      phrase += "afternoon, ";
    } else {
      phrase += "evening, ";
    }
    phrase += name;
  };
  setPhrase();
</script>

<div id="container">
  <div id="greeting">
    <p>{phrase}</p>
  </div>
</div>

<style>
  /* This is the style for the greeting */
  #container {
    background-color: transparent;
    text-align: center;
    position: relative;
    top: 0em;
    text-shadow: 0 2px 3px rgba(0, 0, 0, 0.9);
  }
  #greeting {
    font: 20pt Roboto, Century Gothic;
    color: #fbf9f9;
    text-shadow: 0 0 10px rgba(0, 0, 0, 1);
  }
</style>
