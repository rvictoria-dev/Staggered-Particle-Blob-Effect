# Staggered Particle Blob Effect

### ₊⊹ About

This is a Staggered Particle Blob Effect. It clusters multiple DOM nodes into a cohesive, glowing entity that tracks cursor movement. Its function is to provide highly organic, procedural background interaction, replacing static canvases with an ecosystem of independent, mathematically linked elements.

https://github.com/user-attachments/assets/660edd13-865d-4ff7-85db-26a6d7de92bb

---

### ★ Features

- Cursor tracking
- Staggered animation
- Auto-simulation
- Blend modes

---

### .ᐟ.ᐟ How It Works

- **Particle creation:** JavaScript creates 169 `div` elements (a 13 × 13 grid) inside `#creature`. Each one is a small circle (`border-radius`), with `mix-blend-mode: plus-lighter`, which adds the light from overlapping particles and creates the glow.

- **Proportional size:** `#creature` uses `font-size: 0.2vh`, and all measurements are in `em`. This way, the size of the effect scales with the window height.

- **Blob shape:** With `stagger`, each particle receives different values based on its distance from the center of the grid (`from: “center”`). Those in the center are smaller, lighter, and more opaque, and are positioned on top (`zIndex`). Those at the edges are larger, darker, and nearly transparent, with a fainter shadow. This variation creates the glowing body with soft edges.

- **Follow the cursor:** A timer (`createTimer`) runs 15 times per second and animates all particles toward the cursor's position, which is stored in the `cursor` object.

- **Trail effect:** Each particle starts moving with a longer delay as it moves away from the center (`delay: stagger(40)`), and those on the outside take longer to arrive (`duration: stagger(120)`). When the cursor moves, the center arrives first and the edges lag behind, stretching the blob in an organic way.

- **Blending animations:** The `composition: “blend”` option causes new animations to blend with those still playing, rather than restarting them. This ensures the movement is smooth and seamless.

- **Pulse:** The `pulse` function causes the particles to grow to `scale: 5` in a wave that spreads from the center to the edges, and then return to their original size and opacity in `600 ms`.

- **Automatic movement:** A timeline (`createTimeline`) animates the `cursor` object itself, not the page elements. The `x` axis moves from one side to the other in 3 seconds, and the `y` axis moves up and down in 1 second, in an infinite back-and-forth loop. The `modifier` parameters combine a sine and a cosine wave, and the different durations cause the blob to follow a path that never repeats exactly. The pulse is triggered at the beginning of each loop.

- **Manual control:** On `mousemove` and `touchmove` events, the `followPointer` function calculates the cursor’s position relative to the center of the screen, pauses the automatic movement, and restarts a 1.5-second timer. If the cursor remains still for that duration, the automatic movement resumes on its own.

- **Libraries:** Anime.js is loaded via a CDN (`esm.sh`) using `import`, so the script uses `type=“module”`, and the project requires an internet connection and a local server, such as Live Server.

---

### ⚙️ Tech Stack

- **HTML5** 
- **CSS3** 
- **JavaScript**
- **Anime.js:** animations with `stagger`, timelines, and timers, loaded via CDN (`esm.sh`)

---

### 🖿 Project structure

```
staggered-particle-blob-effect/
├── index.html
├── Styles.css
├── Script.js
└── README.md
```

---

### 📖 What i learned

- **HTML:** Use an empty `div` as a container and let JavaScript create the particles inside it

- **CSS:** Use `em` with `font-size: 0.2vh` so the entire effect scales with the window height

- **CSS:** `mix-blend-mode: plus-lighter` to add the light from overlapping particles and create the glow

- **CSS:** custom properties (`--red`) to define the color in one place

- **JavaScript:** create elements with `createElement` and `appendChild` inside a `for` loop

- **JavaScript:** use ES Modules, with `import` from a library via CDN and `type=“module”` in the script

- **Anime.js:** `stagger` with `grid` and `from: “center”` to assign different values to each particle based on its distance from the center

- **Anime.js:** `createTimer`, `createTimeline`, and `animate` to control the animation timing

- **Anime.js:** `composition: “blend”` so that animations blend together smoothly

- **JavaScript:** reading mouse and touch positions using the `mousemove` and `touchmove` events

- **Debugging:** A script with `import` needs `type=“module”`; otherwise, the browser throws an error and nothing runs

- **Debugging:** The `--red` variable was used in the CSS but wasn't defined, so the color didn't appear

- **Debugging:** Modules don't work when you open `index.html` directly from your computer, so you need to use a local server, such as Live Server
