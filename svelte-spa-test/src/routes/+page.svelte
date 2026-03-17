<script lang="ts">
    import { goto } from "$app/navigation";

    let counter = $state(0);
    let targetPage = $state("");
</script>

<div class="root-layout">
<h1>Svelte SPA Test</h1>
<p>Click the button to increment: {counter}</p>

<div class="flex-column ">
    <button onclick={() => counter++}>Increment</button>
    <button onclick={() => counter = 0}>Reset</button>
    <div>
        <button onclick={() => targetPage && goto(`#/page${targetPage}`)}>Goto Page {targetPage}</button>
        <select bind:value={targetPage}>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
        </select>
    </div>
</div>
</div>

<style>
    .root-layout {
        margin: 0 auto;
        max-width: 500px;
    }

    .flex-column {
        display: flex;
        flex-direction: column;
    }
</style>