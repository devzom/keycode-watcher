<script>
  let key;
  let keyCode;

  function handleKeydown(event) {
    key = event.key;
    keyCode = event.keyCode;
  }

  function copyKeycode() {
    const coppiedMsg = document.getElementById("coppiedMsg");
    coppiedMsg.style.display = "block";

    navigator.clipboard.writeText(keyCode);

    setTimeout(() => {
      coppiedMsg.style.display = "none";
    }, 2000);
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="container">
  <div class="wrapper">
    {#if key}
      <kbd>{key === " " ? "Space" : key}</kbd>
      <p class="keycode">Keycode: <strong>{keyCode}</strong></p>
      <button class="btn-copy" on:click={copyKeycode}>Copy keycode</button>

      <p id="coppiedMsg">Keycode {keyCode} coppied!</p>
    {:else}
      <p>Focus this window and press any key</p>
    {/if}
  </div>
  <div class="copyright">
    Made by <a href="https://jakubzomerfeld.pl">Jakub Zomerfeld</a> in
    <strong>Svelte</strong>
  </div>
</div>

<style>
  .container {
    display: flex;
    height: 100%;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .wrapper {
    text-align: center;
  }

  kbd {
    background-color: #eee;
    border-radius: 4px;
    font-size: 5em;
    padding: 0.1em 0.3em;
    border-top: 5px solid rgba(255, 255, 255, 0.5);
    border-left: 5px solid rgba(255, 255, 255, 0.5);
    border-right: 5px solid rgba(0, 0, 0, 0.2);
    border-bottom: 5px solid rgba(0, 0, 0, 0.2);
    color: #555;
  }

  .keycode {
    font-size: 2em;
    margin-top: 3rem;
  }

  .copyright {
    margin-top: 5rem;
    text-decoration: none;
  }

  #coppiedMsg{
    display: none;
  }
</style>
