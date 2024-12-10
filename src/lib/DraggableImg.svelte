<script lang="ts">
    let props = $props();
    let clicking = $state(false)
    let isMobile = $state(false)
    let x = $state(0)
    $effect(() => {
        isMobile = window.innerHeight > window.innerWidth
    })
</script>

{#if !isMobile}
    <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
    <img {...props}
        role="marquee"
        onmousedown={() => {clicking = true}}  
        onmousemove={(e) => {
            if (clicking && e.target) {
                const xTransform = getComputedStyle(e.target as HTMLImageElement).translate
                console.log(xTransform)
                let x = Number(xTransform.replaceAll('px', ''))
                x += e.movementX;
                console.log(x);
                (e.target as HTMLImageElement).style.translate = x + "px"
            } 
        }}
        draggable="false">
{/if}
<svelte:window onmouseup={() => clicking = false} />


<style>
    img {
        user-select: none;
    }
</style>