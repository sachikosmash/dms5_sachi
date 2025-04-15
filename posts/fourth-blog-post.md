---
title: Chaos
published_at: 2025-03-05
snippet: Creative coding notes and blog
allow math: true
disable_html_sanitization: true
---

# Structure is Perceived Rather than Absolute

In What is Generative Art? Complexity Theory as a Context for Art Theory (2003), Philip Galanter notes that “some maintain that this notion of structure is subjective and remains in the eye of the beholder.” This idea — that structure is perceived rather than absolute — is incredibly useful in the context of generative art, because it frees artists from rigid definitions and allows for a balance between order and randomness in creative expression.

</script>

## highCompressibility() – Checkerboard Pattern

This composition is easily described and predicted: a black and white grid, alternating in a fixed pattern. A computer (and most viewers) recognize the repetition immediately. It’s highly structured, but arguably too predictable to feel interesting. For some, this might appear too mechanical or even boring.

Perceived structure: High, but maybe too obvious or artificial to feel rich.

<iframe id="highCompressibility()" src="https://editor.p5js.org/vubblechi/full/vv6g_-Qrv"></iframe>

<script type="module">

    const iframe  = document.getElementById (`highCompressibility()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

##  lowCompressibility() – Random Noise
This is the opposite: pure randomness. Each pixel is a different brightness. While it's technically complex, it lacks perceivable structure — the human eye struggles to find meaning or pattern. It could represent entropy, chaos, or static.

Perceived structure: Very low — even though it's mathematically complex, people may see “nothing"

<iframe id="lowCompressibility()" src="https://editor.p5js.org/vubblechi/full/nbH0bxlMB"></iframe>

<script type="module">

    const iframe  = document.getElementById (`lowCompressibility()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

## highEffectiveComplexity() – Recursive Branching Tree

This example lives in the sweet spot that Galanter describes:
It’s structured, but not repetitive, complex, but not chaotic. The code uses a recursive function (drawBranch()) with geometric transforms like rotate() and scale to simulate natural growth. The tree is composed of repeating rules, but the variation in angle and scale gives the illusion of organic uniqueness — much like real plants or rivers.

Perceived structure: High — viewers intuitively see form, pattern, and variation.

<iframe id="highEffectiveComplexity()" src="https://editor.p5js.org/vubblechi/full/kwNsIeO2K"></iframe>

<script type="module">

    const iframe  = document.getElementById (`highEffectiveComplexity()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

# high compressibility

<iframe id="highCompressibility()" src="https://editor.p5js.org/vubblechi/full/vv6g_-Qrv"></iframe>

<script type="module">

    const iframe  = document.getElementById (`highCompressibility()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

function setup() {
createCanvas(400, 400);
noLoop();
}

function draw() {
background(255);
let tileSize = 50;

for (let y = 0; y < height; y += tileSize) {
for (let x = 0; x < width; x += tileSize) {
if ((x + y) % (tileSize \* 2) === 0) {
fill(0);
} else {
fill(255);
}
rect(x, y, tileSize, tileSize);
}
}
}

# low compressibility

<iframe id="lowCompressibility()" src="https://editor.p5js.org/vubblechi/full/nbH0bxlMB"></iframe>

<script type="module">

    const iframe  = document.getElementById (`lowCompressibility()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

function setup() {
createCanvas(800, 800);
noLoop();
}

function draw() {
loadPixels();

// Fill every pixel with random colour
for (let y = 0; y < height; y++) {
for (let x = 0; x < width; x++) {
let index = (x + y _ width) _ 4;
let c = random(255); // Random brightness
pixels[index] = c; // Red
pixels[index + 1] = c; // Green
pixels[index + 2] = c; // Blue
pixels[index + 3] = 255; // Alpha
}
}

updatePixels();
}

# high-effective compressibility

<iframe id="highEffectiveComplexity()" src="https://editor.p5js.org/vubblechi/full/kwNsIeO2K"></iframe>

<script type="module">

    const iframe  = document.getElementById (`highEffectiveComplexity()`)
    iframe.width  = iframe.parentNode.scrollWidth
    iframe.height = iframe.width * 9 / 16 + 42

</script>

function setup() {
createCanvas(400, 400);
background(255);
stroke(0);
noFill();
noLoop();

translate(width / 2, height);
drawBranch(100);
}

// Recursive branching function
function drawBranch(len) {
if (len < 4) return;

// Draw one branch
line(0, 0, 0, -len);
translate(0, -len);

// Right branch
push();
rotate(PI / 6);
drawBranch(len \* 0.67);
pop();

// Left branch
push();
rotate(-PI / 6);
drawBranch(len \* 0.67);
pop();
}
