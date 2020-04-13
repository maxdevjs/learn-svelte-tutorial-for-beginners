<script>
  let showModal = true;
  let isPromo = true;
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo}>
    <div class="modal">
      {#if isPromo}
        <p>There is our promo</p>
      {:else}
        <p>Sign up for offers</p>
      {/if}
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

</style>