<script lang="ts">
    import type { PageData } from './$types';

    let { data }: { data: PageData } = $props();
</script>

<header>
    <h1>Portfolio</h1>
    <a href="/">[Back]</a>
</header>
<main>
    <article>
        <h2>Hi!</h2>
        <p>
            Heres a quick look into my portfolio with a couple work-in-progress projects. 
            I'd suggest getting started by looking at the development of <a href="/portfolio/site">this site</a>, 
            but other projects are listed down below.
        </p>
    </article>
    <article>
        <h2>Projects</h2>
        <ul>
            <li>
                <h3>Sorting algorithms</h3>
                <p>All about visualizing sorting algorithms</p>
                <a href="/portfolio/sorting">[Project Link]</a>
            </li>
            <li>
                <h3>Wabbit problem</h3>
                <p>My experiences in the land of bugs bunny.</p>
                <a href="/portfolio/wabbit">[Project Link]</a>
            </li>
            <li>
                <h3>This Site</h3>
                <p>The development of this site</p>
                <a href="/portfolio/site">[Project Link]</a>
            </li>
        </ul>
    </article>
</main>

<style>
    header {
        display: grid;
        grid-template-areas: ". h1 back";
        align-items: center;
        text-align: center;
    }

    header h1 {
        grid-area: h1;
    }

    header a {
        grid-area: back;
    }

    main {
        padding: 3em;
    }
</style>
