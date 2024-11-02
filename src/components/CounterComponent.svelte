<script lang="ts">
  let count = $state(0)
</script>

<div class="counter">
  <input type="number" bind:value={count} disbaled />
  <button onclick={() => count++}>Count</button>
</div>