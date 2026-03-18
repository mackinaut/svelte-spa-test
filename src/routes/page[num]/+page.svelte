<script lang="ts">
    import { goto } from "$app/navigation";
    import { resolve } from "$app/paths";

    let { params } = $props();
</script>

<div class="root-layout">
    <h1>Svelte SPA Test - Page {params.num}</h1>
    <button onclick={() => goto(resolve('/'))}>Go back</button>
</div>

<style>
    .root-layout {
        margin: 0 auto;
        max-width: 500px;
    }
</style>