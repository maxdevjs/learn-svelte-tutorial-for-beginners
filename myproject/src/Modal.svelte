<script>
  // Event Modfiers:
  // once - makes sure the event can only fire once (removes handler)
  // preventDefault - prevent the default action (run e.preventDefault())
  // self - only fires the event if the clicked element is the target
  // ...

  export let message = 'deafult value'; // passed as a prop
  export let showModal = false;
  export let isPromo = false;
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <a href="http://localhost:5000/promo"><p>{message}</p></a>
      <!-- <p>{message}</p> -->
      <!-- {#if isPromo}
        <p>There is our promo</p>
      {:else}
        <p>Sign up for offers</p>
      {/if} -->
    </div>
  </div>
{/if}
<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }

  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }

  .promo .modal {
    background: crimson;
    color: white;
  }
</style>