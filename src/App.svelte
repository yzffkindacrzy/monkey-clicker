<script lang="ts">
  import { onMount } from "svelte";


  let clicks = 0;

  onMount(() => {
    document.getElementById("monkey").onclick = () => {
      clicks += 1
    }
  })
</script>

<main>
  <div class="container"><h1>Monkey Clicker</h1>
    <h2>You have clicked the monkey {clicks} times</h2>
    <img alt="monkey" id="monkey" src="https://media.npr.org/assets/img/2017/09/12/macaca_nigra_self-portrait-3e0070aa19a7fe36e802253048411a38f14a79f8-s1100-c50.jpg" width="50" height="50"/>
  </div>
</main>

<style>
  :root {
    background-color: rgb(249, 97, 97);
  }

  .container {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: gray;
    padding: 20px;
    text-align: center;
    border: 10px solid;
    transition: 350ms
  }

  .container:hover {
    border: 20px solid;
  }

  #monkey {
    transition: 0.3s
  }

  #monkey:hover {
    width: 100px;
    height: 100px;
  }

  #monkey:active {
    width:50px;
    height:50px;
  }
</style>