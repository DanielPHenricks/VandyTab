<!-- This holds a group of buttons (in this case, 4) -->
<script>
  import Button from "./Button.svelte";
</script>

<div class="supporting">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-xs-2" />
      <Button
        linkTitle="https://yes.vanderbilt.edu"
        imageLink="../images/yes.png"
        buttonName="YES"
      />
      <Button
        linkTitle="https://brightspace.vanderbilt.edu"
        imageLink="../images/Brightspace.png"
        buttonName="Brightspace"
      />
      <Button
        linkTitle="https://vanderbilthustler.com"
        imageLink="../images/news.png"
        buttonName="News"
      />
      <Button
        linkTitle="https://get.cbord.com/vanderbilt/full/food_home.php"
        imageLink="../images/food.png"
        buttonName="Order Food"
      />
      <div class="col-xs-2" />
    </div>
  </div>
</div>

<style>
  .container {
    max-width: 56em;
    justify-content: center;
  }
  .supporting {
    text-shadow: 0 2px 3px rgba(0, 0, 0, 0.4);
  }

  .supporting .col-xs-2 {
    top: 0px;
    text-align: center;
    color: #fff;
    margin-bottom: 1em;
  }
</style>
