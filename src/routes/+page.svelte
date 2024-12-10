


<script lang="ts">
    let canvas: HTMLCanvasElement;
    const canvasScalingFactor = 2
    let y = $state(0)
    let angle = $state(0)
    let image: HTMLImageElement

    $effect(() => {
        const canvasStyle = getComputedStyle(canvas);
        canvas.height = Number(canvasStyle.height.replaceAll('px', '')) * canvasScalingFactor
        canvas.width = Number(canvasStyle.width.replaceAll('px', '')) * canvasScalingFactor
        const ctx = canvas.getContext("2d")
        if (!ctx) {
            return
        }
        // ctx.drawImage(refImage, 0, -1000, 1000 * 2, 1800 * 2)
        // ctx.drawImage(refImage2, 1000, 0)
        ctx.fillStyle = "white";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        type Coord = [number, number]

        let squareWidth = 400 - (y / 100)
        let squareHeight = squareWidth * 1.12
        let squareX = (canvas.width - squareWidth) / 2
        let squareY = (canvas.height - squareHeight) / 2 - Math.min(y / 4, window.innerHeight / 4) + 50

        let squareCenterY = squareY + (squareHeight / 2)
        let canvasCenterY = canvas.height / 2
        angle = (canvasCenterY - squareCenterY) / (canvas.height / 10)
        //1-2
        //| |
        //4-3
        let squareCorners: [Coord, Coord, Coord, Coord] = [
            [squareX, squareY],
            [squareX + squareWidth, squareY],
            [squareX + squareWidth, squareY + squareHeight],
            [squareX, squareY + squareHeight],
        ]
        ctx.lineWidth = 5
        ctx.beginPath();
        ctx.moveTo(0, 0);
        ctx.lineTo(...squareCorners[0]);

        ctx.moveTo(canvas.width, 0)
        ctx.lineTo(...squareCorners[1]);

        ctx.moveTo(canvas.width, canvas.height)
        ctx.lineTo(...squareCorners[2]);

        ctx.moveTo(0, canvas.height)
        ctx.lineTo(...squareCorners[3]);

        ctx.moveTo(...squareCorners[3])
        for (const [x, y] of squareCorners) {
            ctx.lineTo(x, y)
        }

        
        ctx.stroke();
        const scale = 0.7 - Math.min(y / 10000, 5);
        const imgHeight = image.height * scale
        const imgWidth = image.width * scale
        ctx.drawImage(image, 
            (canvas.width - imgWidth) / 2, 
            (canvas.height - imgHeight) / 2 + 50 + (y / 100), 
            imgWidth, 
            imgHeight)
        // second draw with offset gives glitchy-effect
        ctx.drawImage(image, 
            (canvas.width - imgWidth) / 2 - Math.max(5, (y / 170)), 
            (canvas.height - imgHeight) / 2 + 50 + (y / 100), 
            imgWidth, 
            imgHeight)


    })
</script>

<main>
    <img src="/path862.png" alt="cryptid" hidden bind:this={image}>
    <div class="fixed">
        <div class="container">
            <a href="/home" class="home" style={`--dx: ${angle}`}>Home Page</a>
            <a href="/resume" class="resume" style={`--dx: ${angle}`}>Resume</a>
            <a href="/portfolio" class="portfolio" style={`--dx: ${angle}`}>Portfolio</a>
            <canvas bind:this={canvas}></canvas>
        </div>
    </div>
    <div class="scroll-content">Welcome</div>
</main>

<svelte:window bind:scrollY={y} />

<style>
    div {
        display: grid;
        place-items: center;
        background-color: black;
    }

    .fixed {
        position: fixed;
        width: 100%;
    }

    .container {
        position: relative;
    }

    canvas {
        z-index: 0;
        height: min(100vh, 100vw);
        width: min(100vh, 100vw);
        border: solid black 1px;
        box-sizing: border-box;
    }

    a {
        font-family: 'Times New Roman', Times, serif;
        font-size: 5em;
        position: absolute;
        z-index: 9000;
        --dx: -50;
    }
    .home {
        top: 0px;
        transform: perspective(400px) rotateX(calc(-51deg - (var(--dx) * 7deg)));
    }
    .resume {
        bottom: 0px;
        transform: perspective(400px) rotateX(calc(50deg - (var(--dx) * 7deg)));
    }
    .portfolio {
        right: 0px;
        transform: perspective(600px) rotateY(-49deg) rotateZ(calc(var(--dx) * 7deg)) rotateX(calc(1deg));
        transform-origin: 100% 100%;
    }

    .scroll-content {
        height: max(200vw, 200vh);
    }
</style>