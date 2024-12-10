<script lang="ts">
    import type { PageData } from '../../portfolio/site/$types';

    let { data }: { data: PageData } = $props();
</script>

<header>
    <span></span>
    <h1>About this site</h1>
    <nav>
        <a href="/portfolio">[Back to Portfolio]</a>
        <a href="/">[Back to Navigation]</a>
    </nav>
</header>
<main>
    <figure class="svelte">
        <img src="/svelte.svg" alt="Svelte logo">
        <figcaption>The Svelte logo taken from <a href="https://svelte.dev/">svelte.dev</a></figcaption>
    </figure>
    <article>
        <h2>The tools I used to make this website</h2>
        <p>
            This website is made using <a href="https://svelte.dev/docs/svelte/overview">Svelte 5</a>, 
            <a href="https://svelte.dev/docs/kit/introduction">SvelteKit 2</a>, 
            and a lot of the css was originally written with <a href="https://sass-lang.com/">Sass</a>.
            Svelte is one of my preferred frameworks, namely, due to its ease and similarity to raw html.
            While the css appears to be embedded in the .svelte file, 
            its usually exported as a separate file in the final build, which was a project/assignment requirement. 
        </p>
    </article>
    <article>
        <h2>First Sketches</h2>
        <p>
            I recently became familiar with the term pantser; a writer that does not write plan the plot prior to writing.
            This word describes not only my writing style, but also how I prefer to code and how I designed this UI.
            In general, I write and code off the top of my head. 
            I did make some sketches ahead of time, as the project/assignment requirements demanded it,
            and its nice to see what I planned come to fruition.
        </p>
        <img class="sketch" src="/1000004995.jpg" alt="Idea Sketch">
        <img class="sketch" src="/1000004996.jpg" alt="Home page Sketch">
        <img class="sketch" src="/1000004997.jpg" alt="Navigation Sketch">
        <p>
            I think of programming as an art form to some extent.
            Theres not usually a 'correct' way to do things at a high level, rather, tradeoffs with each choice.
            I think, because of my awareness of those tradeoffs, 
            I don't fall into the same pitfalls that conventional artists do, 
            where they see the gap between the image of their work, and the realization of their work.
        </p>
        <figure class="picasso">
            <img src="/202331Picasso-768x778.jpg" alt="A picasso work">
            <figcaption>
                Picasso as a young cubist: a self-portrait by Pablo Picasso from 1907, one of 13,500 paintings the artist completed during his lifetime. Photo by Bridgeman Images / DACS
            </figcaption>
        </figure>
    </article>
    <article>
        <h2>Design Choices</h2>
        <h3>Svelte</h3>
        <p>
            Choosing Svelte was an incredibly difficult decision for this project. 
            Since this project is for an assignment to an introductory class to web development,
            I felt very apprehensive about bringing a full stack web meta-framework like SvelteKit into the project cycle.
            While it was a difficult decision, I don't regret it. 
            Svelte comes with numerous features, and some that are especially pertinent to this project, such as
        </p>
        <ul>
            <li>
                <h4>Hot reloading with <a href="https://vite.dev/">Vite</a>. </h4>
                While the course suggests the 
                <a href="https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer">Live Server Vscode Extension</a>,
                Its not as responsive or as fast as Vite, and it didn't have preprocessing for Sass, which was needed for early development.
            </li>
            <li>
                <h4>Accessibility checker with <a href="https://www.a11yproject.com/">a11y</a>.</h4>
                A assignment/project requirement was that it needed to be accessible, and responsive on mobile devices.
                A11y's semantic checker helped me find accessibility issues during development, 
                which is much faster than copy and pasting the code into an online checker, 
                or repeatedly doing lighthouse reports on the website.
                <blockquote>
                    <b>Fun fact</b>: a<span class="times">11</span>y is short for accessibility! 
                    A common thing in the developer space is to shorten words by taking the first and last letter, 
                    and then putting the number of removed letters in the middle.
                    <div>Internationalization becomes I-nternationalizatio-n, which becomes I<b class="times">18</b>n.</div>
                </blockquote>
            </li>
            <li>
                <h4>Simple, reactive, declarative code with templates.</h4>
                The core of any javascript framework is reactive code, and that enabled me to create animations
                and little islands of interactivity throughout the project.
            </li>
        </ul>
        <p></p>
        <h3>Sass</h3>
        <p>
            One of the big design choices/refactors I made in the project was removing Sass.
            As much as I love preprocessors, a lot of the .scss files weren't fully utilizing sass and I decided to manually refactor all of the css.
        </p>
        <h3>Typescript</h3>
        <p>
            Another less notable design choice was the integration of typescript. 
            It made sense given where the project was going, 
            and jsdoc comments were cumbersome enough to render typescript a necessity.
        </p>
    </article>
    <article>
        <h2>Final Product</h2>
        <p>
            The site more or less turned out exactly as I wanted, with a few hijinks.
            A large issue I faced throughout was the short span of time I gave myself for this project.
            As a challenge(<i>"challenge"</i>), I tried to complete this project as fast as humanly possible.
        </p>
        <h3>Portfolio</h3>
        <p>
            Given the period of time I allotted for this project, I couldn't finish many of the portfolio projects.
            One of the projects I really wanted to incorporate was an emulator for my vim config.
            While I have made <a href="https://www.vim.org/">vim</a> in the past(not to spec, but close enough), 
            I lost the hard drive with the original files.
            Such a project is long and arduous, but not impossible in this span of time.
        </p>
    </article>

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
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    figure.svelte {
        width: 75%;
    }
    figure.svelte figcaption {
        padding: 1em;
        font-size: 0.7em;
        color: grey;
        text-align: center;
    }
    article {
        padding: 1em 10%;
    }
    article p {
        padding: 1em;
    }
    .times {
        font-family: 'Times New Roman', Times, serif;
    }
    figure.picasso {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    figure.picasso img {
        max-width: 50%;
    }
    figure.picasso figcaption {
        width: 90%;
    }
    img.sketch {
        width: 30%;
    }
</style>