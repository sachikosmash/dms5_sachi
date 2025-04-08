---
title: My introduction to creative coding as a noob! 
published_at: 2025-04-04
snippet: 1.1 Homework and Notes
disable_html_sanitization: true
allow_math: true
---
# My introduction to creative coding as a noob 

My first attempt at making a grid:

<iframe id="static_squares" src="https://editor.p5js.org/vubblechi/full/Dy6k23zZT"></iframe>

<script type="module">

    const iframe  = document.getElementById (`static_squares`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

I realised that I can just repeat the code to create the stacking effect:

<iframe id="moving_squares" src="https://editor.p5js.org/vubblechi/full/gsVp-UMu8"></iframe>

<script type="module">

    const iframe  = document.getElementById (`static_squares`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

## Transcription of nots from the 5th of March 2025 

.md means "markdown" (markdown syntax)
at the top of markdown code is what you call, front matter 
front matter is used to identify meta data 
metadata: describes data such as format 

p5.js functions:

define a 'setup ()' function 

setup () function only runs 1x
draw () function only runs after the setup function and loops 

# Rafaël Rozendaal

i realised that the blocks change colors and positions in response to user interactions. 

It was probably done by dividing the canvas  into a grid where each cell represents a block. Each block would have dimensions based on the canvas size  and number of rows and columns.

Then, using mouse click functions, must likely hovering, whilst assigning colours for each box. It seems to be generated randomly. 

to replicate this, I will need to setup the canvas and the grid system, learn how to draw rectangles using p5.js and get comfortable with using loops and arrays. 

Animation would be used by applying frame rate control. 

<iframe id="interactive_sq" src="https://editor.p5js.org/vubblechi/full/YzQ_oPBBl"></iframe>

<script type="module">

    const iframe  = document.getElementById (`static_squares`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

//hover onto canvas to interact

// setting up grids as a global variable
let cols = 10; 
let rows = 10;
let blockSize;
let colors = []; //empty array for colour random

function setup() {
  createCanvas(400, 400);
  blockSize = width / cols;
  for (let i = 0; i < cols * rows; i++) {
    colors.push(color(random(255), random(255), random(255)));
  }
}

function draw() {
  background(0);
  for (let y = 0; y < rows; y++) {
    for (let x = 0; x < cols; x++) {
      let index = x + y * cols;
      let blockX = x * blockSize;
      let blockY = y * blockSize;
      
      if (mouseX > blockX && mouseX < blockX + blockSize && 
          mouseY > blockY && mouseY < blockY + blockSize) {
        colors[index] = color(random(255), random(255), random(255));
      }
      
      fill(colors[index]);
      rect(blockX, blockY, blockSize, blockSize); //rectangle block
    }
  }

# This is h1

![a drippy lemon](logo.svg)

^ images are written like this: `![description](file_path/file_name.png)`

## This is h2

*This is italic.*[^1]

[^1]: This is a footnote, *which can also be italic*.

**This is bold.**

Hyperlinks can be written like this: `[text](https://URL)`

You can find a markdown cheat-sheet [here](https://www.markdownguide.org/cheat-sheet/).

## Maths:

... which can be written inline, like this: $\{ x, y, z \} \in \N$

... or block, like this:

$$ x^2 + y^2 = z^2 $$

Visit [ $\KaTeX$ ](https://katex.org/docs/supported#fractions-and-binomials) for more information about writing maths.

## Embedding video:

<iframe id="coding_train_video" src="https://www.youtube.com/embed/rI_y2GAlQFM?si=RDgjkpunxk1mQzMI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<script type="module">

    console.log (`hello world! 🚀`)

    const iframe  = document.getElementById (`coding_train_video`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16

</script>

## Embedding p5 sketches:

<iframe id="falling_falling" src="https://editor.p5js.org/capogreco/full/Fkg05m7aA"></iframe>

<script type="module">

    const iframe  = document.getElementById (`falling_falling`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

## Canvas API

<canvas id="canvas_example"></canvas>

<script type="module">
    const cnv = document.getElementById (`canvas_example`)
    cnv.width = cnv.parentNode.scrollWidth
    cnv.height = cnv.width * 9 / 16

    const ctx = cnv.getContext (`2d`)
    const pos = {
        x: -100,
        y: cnv.height / 2 - 50
    }
    
    function draw_frame () {
        ctx.fillStyle = `turquoise`
        ctx.fillRect (0, 0, cnv.width, cnv.height)

        ctx.fillStyle = `hotpink`
        ctx.fillRect (pos.x, pos.y, 100, 100)

        pos.x += 2

        if (pos.x > cnv.width) {
            pos.x = -100
        }

        requestAnimationFrame (draw_frame)
    }

    draw_frame ()
</script>


