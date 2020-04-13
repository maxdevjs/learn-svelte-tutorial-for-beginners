<script>
  export let message = 'deafult value'; // passed as a prop
  export let showModal = false;
  export let isPromo = false;
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo} on:click>
    <div class="modal">
      <p>{message}</p>
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