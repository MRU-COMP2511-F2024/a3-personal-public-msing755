<script lang="ts">
    import type { PageData } from './$types';

    let { data }: { data: PageData } = $props();
</script>

<header>
    <span></span>
    <h1>Sorting algorithms</h1>
    <nav>
        <a href="/portfolio">[Back to Portfolio]</a>
        <a href="/">[Back to Navigation]</a>
    </nav>
</header>
<main>
    Something about sorting algorithms...
</main>


<style>
    header {
        display: grid;
        grid-template-areas: ". h1 back";
        grid-template-columns: 1fr auto 1fr;
        align-items: center;
        text-align: center;
    }

    header h1 {
        grid-area: h1;
    }

    header nav {
        grid-area: back;
        display: flex;
        flex-direction: row-reverse;
    }
</style>