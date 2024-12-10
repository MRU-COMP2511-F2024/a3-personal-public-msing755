<script lang="ts">
    import type { Snippet } from 'svelte';
    import type { LayoutData } from './$types';

    let { data, children }: { data: LayoutData, children: Snippet } = $props();
    // let isPortfolioRoot = $state(false)
    // $effect(() => {
    //     isPortfolioRoot = window.location.href.split('/').at(-1) == 'portfolio'
    // })
    
</script>

<!-- <header>
    <span></span>
    <h1>About this site</h1>
    <nav>
        {#if !isPortfolioRoot}
        <a href="/portfolio">[Back to Portfolio]</a>
        {/if}
        <a href="/portfolio">[Back to Navigation]</a>
    </nav>
</header> -->
{@render children()}