<script lang="ts">
  import { onMount } from "svelte";

  let bananas;

  let devMode = false;

  if (localStorage.getItem("bananas")) { bananas = parseInt(localStorage.getItem("bananas")) } else {bananas = 0}

  onMount(() => {
    document.getElementById("monkey").onclick = () => {
      bananas += 1;

      var audio = new Audio('pop.mp3');
      audio.play();
    };

    document.getElementById("buy-autoclicker").onclick = () => {
      if (!(bananas >= 10)) return;
      bananas -= 10;

      setInterval(() => {
        bananas += 1;
      }, 3000);
    };

    document.getElementById("buy-farmer").onclick = () => {
      if (!(bananas >= 50)) return;
      bananas -= 50;

      setInterval(() => {
        bananas += 5;
      }, 1000);
    };

    document.getElementById("buy-zookeeper").onclick = () => {
      if (!(bananas >= 250)) return;
      bananas -= 250;

      setInterval(() => {
        bananas += 10;
      }, 500);
    };

    document.getElementById("buy-fbi").onclick = () => {
      if (!(bananas >= 1500000)) return;
      bananas -= 1500000;

      setInterval(() => {
        bananas += 20000;
      }, 1)
    }

    window.addEventListener("unload", () => {
        localStorage.setItem("bananas", bananas)
    })
  });
</script>

<main>
  <div class="container">
    <h1>Monkey Clicker</h1>
    <h2>You have {bananas} bananas</h2>
    <h3>Made by Yusof</h3>
    <img
      alt="monkey"
      id="monkey"
      src="https://media.npr.org/assets/img/2017/09/12/macaca_nigra_self-portrait-3e0070aa19a7fe36e802253048411a38f14a79f8-s1100-c50.jpg"
      width="50"
      height="50"
    />
    <div id="upgrades">
      <h2>Upgrades</h2>
      <div id="autoclicker" class="upgrade">
        <h3>Autoclicker</h3>
        <h3>Cost 10 bananas</h3>
        <button id="buy-autoclicker">Buy</button>
      </div>
      <div id="farmers" class="upgrade">
        <h3>Farmers</h3>
        <h3>Cost 50 bananas</h3>
        <button id="buy-farmer">Buy</button>
      </div>
      <div id="zookeepers" class="upgrade">
        <h3>Zookeeper</h3>
        <h3>Cost 250 bananas</h3>
        <button id="buy-zookeeper">Buy</button>
      </div>
      <div id="fbi" class="upgrade">
        <h3>FBI</h3>
        <h3>Cost ??? bananas</h3>
        <button id="buy-fbi">Buy</button>
      </div>
    </div>
    {#if devMode}
      <div id="devtools">
        <h1>Devtools</h1>
        <button on:click={() => {bananas += 100000}} style="background-color: red;">Add 100000 Bananas</button>
        <button on:click={() => {bananas = 0}} style="background-color: red;">Reset Bananas</button>
      </div>
    {/if}
  </div>
</main>

<style>
  :root {
    background-color: rgb(255, 255, 255);
  }

  #devtools {
    border: 5px solid;
    margin: auto 15;
    display: inline-block;
  }

  button {
    padding: 10px;
    background-color: gray;
    border: none;
    transition: 350ms;
  }

  button:hover {
    padding: 15px;
  }

  .container {
    background-color: gray;
    padding: 30px;
    text-align: center;
    border: 10px solid;
    transition: 350ms;
  }

  .container:hover {
    border: 20px solid;
  }

  #upgrades {
    background-color: gray;
    padding: 10px;
    text-align: center;
    border: 10px solid;
    transition: 350ms;
  }

  #upgrades:hover {
    border: 20px solid;
  }

  .upgrade {
    padding: 5px;
    background-color: purple;
    border: 5px solid;
  }

  #monkey {
    transition: 0.3s;
    border: 2px solid;
  }

  #monkey:hover {
    width: 100px;
    height: 100px;
  }

  #monkey:active {
    width: 50px;
    height: 50px;
  }
</style>
