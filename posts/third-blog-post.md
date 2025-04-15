---
title: Sound, Interaction and Style
published_at: 2025-03-05
snippet: Creative coding notes and blog
allow math: true
disable_html_sanitization: true
---

🔹 1. Variables
Variables are used to store data that the program can use and modify.

Examples:

let spirits = []; — stores all the Spirit objects created.

let isRaining = false; — tracks whether it’s currently raining.

let osc; — stores the sound oscillator.

Inside the Spirit class: variables like x, y, velX, hover, size, etc., define each spirit's behaviour and appearance.

🔹 2. Functions
Functions organise blocks of code to perform specific tasks, which can be reused.

Examples:

setup() and draw() — core p5.js functions that initialise and continuously update the canvas.

mousePressed() — triggers new spirits on click.

playCutePop() — encapsulates the pop sound behaviour.

Inside the Spirit class: methods like applyKinship(), update(), and display() define what each spirit does.

🔹 3. Iteration
Iteration refers to loops that repeat actions over collections or a number of times.

Examples:

for (let spirit of spirits) — loops over all spirits to reset their state.

for (let i = 0; i < spirits.length; i++) — applies forces and updates each spirit.

for (let i = 0; i < 5; i++) — used to draw multiple fuzzy outlines for fuzzy spirits.

Rain is created using:

js
Copy
Edit
for (let i = 0; i < 100; i++) {
rainDrops.push(createVector(random(width), random(height)));
}
🔹 4. Boolean Logic
Boolean logic involves true/false values and is often used in if statements to control the flow.

Examples:

if (!isRaining && now - lastRainEndTime > timeBetweenRain && random(1) < 0.001) — starts rain based on multiple boolean conditions.

if (d < this.currentSize / 2) — detects if the mouse is hovering over a spirit.

if (this.isBlinking && now - this.lastBlinkTime > this.blinkDuration) — controls blinking behaviour.

Used to toggle glow effects with if (this.isConnected).

🔹 5. Arrays
Arrays are used to store lists of data.

Examples:

spirits[] — holds all the spirit objects currently active.

rainDrops[] — stores coordinates of falling rain particles.

types = ['blob', 'mushroom', 'fuzzy'] — used to randomly assign spirit types.

🔹 6. Classes
Classes are blueprints for creating objects with shared structure and behaviour.

Example:

The Spirit class defines how each spirit looks, moves, and interacts:

constructor() — sets up initial properties like position, colour, and size.

applyKinship() — adds attraction/repulsion between spirits.

update() — controls movement and animations.

display() — draws each spirit differently based on type, hover, and connection.

# Reflections

🌸 With regard to AT1, here's how I aim to achieve the aesthetic register of cute in my interactive sketch:
🔮 Visually:
Pastel colour palette: A soft, warm background in pastel pink (#fdf2f8) and randomly-generated spirit colours in gentle blues, pinks, and purples (RGB 150–255 ranges) help create a calm and non-threatening visual world.

Round, squishy shapes: All spirit types (blob, mushroom, fuzzy) use circular or puffy shapes with soft edges to enhance the feeling of approachability and cuteness.

Small facial features: Big, round eyes and gentle smiles with slight expressions (like smiling more when connected) draw from the "baby schema" principle of cuteness.

Glow effects: Spirits glow softly when connected, adding a magical quality, which is common in kawaii aesthetics.

Floating/breathing animation: Spirits gently bounce and "breathe", giving them a soft, living presence, like jellyfish or floating fairies.

Blinking: Spirits blink every 2–8 seconds, enhancing lifelikeness in a soft, humorous way.

🎵 Sonically:
Sine wave pops: Each spirit spawn is accompanied by a soft, high-pitched "pop" using sine waves (osc.freq(random(400, 800))), which is a simple and non-aggressive sound type often used in playful, toy-like interfaces.

Pop dynamic: The amplitude rises and fades quickly to avoid harshness, mimicking the sound of a bubble popping, which is commonly associated with cuteness or child-like visuals.

Silent baseline: Silence dominates the sketch unless actions happen, creating space for delicate interactions to stand out more.

💫 Interactively:
Mouse-click spawns a friend: Every click results in a new spirit appearing with a sound effect—this reinforces a reward cycle of gentle cause-and-effect.

Spirits interact with each other: Through attraction/repulsion forces, spirits appear to form social bonds—when close, they glow and smile more, simulating emotional "cuteness" through relationships.

Hovering feedback: Spirits grow eyes when hovered over, showing they are aware of the player and reacting in a friendly way.

Random rain: Periodic, soft rain events make the world feel dynamic and alive, yet it's not harsh or disruptive—rather, a soft environmental change.

🧑‍🤝‍🧑 Colleague Feedback:
I showed the sketch to a classmate and asked them how well it achieves the cute aesthetic. Here's their feedback for each category:

Visual Feedback:
"The pastel palette and floaty animations are super cute, especially the way they breathe. The blinking adds so much personality. The mushroom cap and fuzzy spirit are my favourites!"

✅ Cuteness Level: High
💡 Suggestion: Add little cheeks (blush spots) or hats/accessories for more individuality.

🛠️ JS Implementation Tip:

Add a drawCheeks() method or randomised accessory props in Spirit.display():

js
Copy
Edit
fill(255, 182, 193, 120); // soft pink
ellipse(-eyeXOffset, eyeYOffset + 5, 6, 4);
ellipse(eyeXOffset, eyeYOffset + 5, 6, 4);
Sonic Feedback:
"The pop sound is gentle and satisfying, fits the soft mood. I wish there were more varied cute sounds, like tiny giggles or twinkles when spirits connect."

✅ Cuteness Level: Medium-High
💡 Suggestion: Add sparkly chimes or a "laugh" tone when spirits touch.

🛠️ JS Implementation Tip:

Use multiple p5.Sound files or FM synthesis tones. Trigger additional sounds inside checkConnections():

js
Copy
Edit
if (s1.connectionCount === 1) {
cuteChime.play(); // preload & trigger once per new connection
}
Interactive Feedback:
"Clicking to spawn and seeing them interact feels alive, like making new friends! I’d love to see them react when you drag or touch them too."

✅ Cuteness Level: High
💡 Suggestion: Add interactivity beyond spawning—e.g., dragging spirits, or making them cuddle if clicked twice.

🛠️ JS Implementation Tip:

Add a mouseDragged() event and check if mouse is near a spirit:

js
Copy
Edit
function mouseDragged() {
for (let spirit of spirits) {
if (dist(mouseX, mouseY, spirit.x, spirit.y) < spirit.currentSize / 2) {
spirit.baseX = mouseX;
spirit.baseY = mouseY;
}
}
}

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
