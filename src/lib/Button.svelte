<!-- This is the code for one button. -->
<script>
  export let linkTitle;
  export let imageLink;
  export let buttonName;
</script>

<div class="col-sm-2">
  <a href={linkTitle}>
    <img
      class="buttonImage"
      src={imageLink}
      height="65"
      width="65"
      alt="link"
    />
  </a>
  <p>{buttonName}</p>
</div>

<style>
  .col-sm-2 {
    top: 0px;
    text-align: center;
    color: #fff;
    margin-bottom: 1em;
  }
  .buttonImage {
    -webkit-transition-duration: 0.2s;
    -moz-transition-duration: 0.2s;
    transition-duration: 0.2s;
    -moz-box-shadow: 0 0 10px rgba(255, 255, 255, 1);
    -webkit-box-shadow: 0 0 10px rgba(255, 255, 255, 1);
    box-shadow: 0 0 10px rgba(255, 255, 255, 01);
    border: solid 1px #fff;
    border-radius: 10px;
  }
  p {
    display: block;
    text-align: center;
    width: 100%;
    font-family: Roboto, sans-serif;
    font-weight: 400;
    opacity: 0.9;
    font-size: 0.9em;
    text-shadow: 0 0 4px rgba(0, 0, 0, 0.5);
    color: #fff;
  }
</style>
