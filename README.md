# Órbita — un pequeño universo

An interactive blue galaxy on a dark background, built as a single, self-contained HTML page. Move the pointer through the stars to bend their paths, or hold it down to create a stronger gravitational pull.

The interface is in Spanish. The page runs entirely in the browser, including offline, with no external assets, libraries, build step, or backend.

## Open locally

1. Clone the repository:

   ```sh
   git clone https://github.com/jordi-torras-ai/aden-astra-oct.git
   cd aden-astra-oct
   ```

2. Open `index.html` in a modern browser. On macOS:

   ```sh
   open index.html
   ```

You can also download the repository as a ZIP, extract it, and double-click `index.html`. No local server is required.

## Controls

| Action | Result |
| --- | --- |
| Move the mouse over the galaxy | Attract nearby stars and gently shift the perspective. |
| Hold the primary mouse button | Increase the attraction. |
| Touch and drag | Move the gravitational field on a touch screen. |
| **Pausar / Reanudar** | Pause or resume the animation. |
| **Ajustes → Gravedad** | Change the attraction from 0× to 2.5×. |
| **Ajustes → Velocidad** | Change the galaxy's rotation and twinkle speed from 0.2× to 2×. |
| **Restablecer universo** | Restore the star arrangement and default settings. |
| **Solo galaxia** | Hide the interface; use **Mostrar controles** to bring it back. |

Keyboard controls are available when the galaxy canvas has focus:

- **Arrow keys:** move the gravitational field.
- **Space:** pause or resume.
- **H:** hide or show the interface.
- **Escape:** close settings, leave immersive mode, and release the gravitational field.

When the operating system requests reduced motion, the page starts paused. Select **Reanudar** to animate it. Animation also stops while the browser tab is hidden.

## How it works

- Canvas 2D renders a tilted, three-armed spiral with 3,600–7,200 stars, chosen according to the viewport when the galaxy is generated.
- Procedural sprites provide blue gradients, soft halos, and occasional diffraction spikes. A final blue tint keeps overlapping glows from turning white.
- A local attraction field and tangential force make stars swirl around the pointer. Damping and a restoring force let them return toward their original paths.
- Cached sprites and a cached background reduce drawing overhead; device pixel ratio is capped at 2.

The gravity is an artistic interaction, rather than an astronomical simulation.

## Project structure

```text
index.html   Page markup, styles, rendering, and interaction
README.md    Setup and controls
.gitignore   Local files and browser-test artifacts excluded from Git
```

To customize the effect, edit `index.html`: `palette` controls star colors, `populate()` creates the star distribution, and `draw()` handles motion, interaction, and rendering.

## Manual verification

After editing, check mouse hover and press, touch dragging, pause/resume, both sliders, reset, and immersive mode. Check narrow portrait and landscape viewports, keyboard navigation, and reduced-motion mode. Open the file without a network connection to confirm that it remains self-contained.

The initial implementation was checked in Chromium with desktop and emulated touch viewports, including reduced motion and offline loading. There is no automated test suite or cross-browser certification.

## Inspiration

The moving star field in [OpenAI's GPT-6 Astra announcement](https://openai.com/es-ES/index/gpt-6-astra/) inspired the visual direction. This implementation draws its own stars procedurally, using a blue palette.
