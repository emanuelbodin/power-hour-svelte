<script lang='ts'>
    import { timer, time, isRunning, isComplete } from "$lib/stores/timer";

</script>

<div class="text-white text-2xl">{$time}</div>
  <div class="buttons">
    {#if !$isComplete}
      {#if $isRunning}
        <button class='btn btn-outline btn-warning' on:click={() => timer.pause()}>pause</button>
      {:else}
        <button class='btn btn-outline btn-success' on:click={() => timer.start()}>start</button>
      {/if}
    {/if}
  </div>