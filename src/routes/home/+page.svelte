<script lang="ts">
    import type { PageData } from './$types';

    let { data }: { data: PageData } = $props();

    let clicking = $state(false)
    let isMobile = $state(false)
    let iframe: HTMLIFrameElement

    $effect(() => {
        isMobile = window.innerHeight > window.innerWidth
        if (iframe.contentWindow) {
            iframe.height = iframe.contentWindow.document.body.scrollHeight + "px";
        }
    })

    const draggable = {
        role: "marquee",
        onmousedown: () => {clicking = true},
        onmousemove: (e: MouseEvent) => {
            if (clicking && e.target) {
                console.log('hello')
                const xTransform = getComputedStyle(e.target as HTMLImageElement).translate || '0px'
                let x = Number(xTransform.replaceAll('px', ''))
                if (isNaN(x)) {
                    x = 0
                }
                x += e.movementX;
                (e.target as HTMLImageElement).style.translate = x + "px"
            } 
        },
    }
</script>


<header>
    <span></span>
    <h1>
        Homepage.htm
    </h1>
    <a href="/">[Back]</a>
</header>

<main>
    <video controls>
        <source src="/469809101_8957130804348926_5146062620329518980_n.mp4" type="video/mp4">
        <track kind="captions">
    </video>

    <article class="cluttered">
        <h2 class="large-text">Sorry, its a little cluttered,</h2>
        <p>
            But despite the mess, I think its a pretty cool site. 
        </p>
        <p>
            Hi, I'm Mehtab. I've been a programmer for well over 5 years with experience all over the place, 
            from writing web socket servers in rust, making a desktop app in c, to the wide array of websites that I've never deployed.
            You can contact me on my github, or via email using the form <a href="#contact">below</a>.
        </p>
        <p>
            I made this portfolio site for an assignment, I used svelte 5 with sveltekit and sass. 
            You can read more about this project in my <a href="/portfolio/site">portfolio</a>.
            I'm generally a pretty big dreamer, and some of the ideas I had were too cumbersome in raw javascript, 
            and so I brought in a framework to do the heavy lifting.
        </p>
        <p>
            While bringing in a fullstack web framework for an assignment to an introductory course kinda feels like cheating, 
            I think the features I added made it worthwhile. 
        </p>

        <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
        {#if !isMobile}

            <img src="/canadian-pacific-rail.jpg" alt="" {...draggable} draggable="false" class="draggable" style="left: 0px;">
            <img src="/cats.JPEG" alt="" {...draggable} draggable="false" class="draggable" style="left: 10%; top: -10%">
            <img src="/peach.JPEG" alt="" {...draggable} draggable="false" class="draggable" style="top: 40%;z-index: 9; left: 50%">
            <img src="/tree.jpg" alt="" {...draggable} draggable="false" class="draggable" style="height: 80%; top: 50%;">
            <img src="https://ca-times.brightspotcdn.com/dims4/default/23e84ab/2147483647/strip/true/crop/3000x3000+0+0/resize/2000x2000!/quality/75/?url=https%3A%2F%2Fcalifornia-times-brightspot.s3.amazonaws.com%2F87%2F1a%2F94476b83484c95c10f864080ae0c%2Fgettyimages-2708609.jpg" alt="" {...draggable} draggable="false" class="draggable" style="right: 0px; top: 5%;">
        {/if}

    </article>

    <article class="contact">
        <h2 id="contact">Contact:</h2>
        <iframe title="Contact" src="/contact" frameborder="0" bind:this={iframe}></iframe>
    </article>

    <article class="other">
        <h2>Other:</h2>
        <p>You can also check out my <a href="/resume">resume</a>, or watch the DVD below.</p>
        <!-- svelte-ignore a11y_distracting_elements -->
        <marquee
            direction="down"
            width="500"
            height="280"
            behavior="alternate"
            class="dvd">
            <marquee behavior="alternate">
                    <img src="/dvdlogo-06.svg" alt="DVD logo" width="60">
            </marquee>
        </marquee>
    </article>
</main>
<svelte:window onmouseup={() => clicking = false} />



<style>
    video {
        width: 60%;
        aspect-ratio: 1;
    }

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        text-align: center;
        padding: 0em 5em;
    }

    header a {
        text-align: center;
        height: 10px;
    }

    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        overflow-x: hidden;
    }

    article.cluttered {
        padding: 4em 10%;
        position: relative;
    }
    article.cluttered img.draggable {
        user-select: none;
        position: absolute;
        top: 0px;
        max-width: 400px;
        min-width: 20%;
    }
    article {
        padding: 4em;
        box-sizing: border-box;
        width: 100%;
    }
    
    h2 {
        text-align: center;
    }

    h2.large-text {
        font-size: 5em;
    }

    article.other, article.contact {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    
    marquee.dvd {
        max-width: 100%;
        border:solid
    }
    

</style>
