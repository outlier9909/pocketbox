# Contributing to pocketbox

pocketbox is small by design.
Please read this before opening a PR.

---

## Core principles (non-negotiable)

1. **Feel over features**
2. **Deterministic timing**
3. **No blocking in the main loop**
4. **Simulation first, rendering second**
5. **Cheap hardware is a feature, not a limitation**

If a change violates these, it probably doesn’t belong.

---

## Code conventions

### Language
- C (Pico SDK)
- C11
- No C++

### Naming
- `snake_case` for functions and variables
- File prefixes indicate responsibility:
  - `platform_*.c` — hardware, drivers
  - `core_*.c` — time, input, simulation
  - `render_*.c` — scanline rendering, visuals

### Units
- Time: **seconds** (`float`)
- Angles: radians
- Coordinates: screen space unless stated otherwise

### Memory
- No dynamic allocation (`malloc`) in the main loop
- Static buffers preferred
- Stack usage should be conservative

---

## Runtime contract

All games built on pocketbox must respect:

- A `dt`-based update loop
- No blocking delays
- Rendering performed via scanlines
- Input processed before simulation
- Simulation updated before rendering

Breaking these assumptions will cause subtle bugs.

---

## Rendering rules

- Rendering must be deterministic
- Rendering must not mutate simulation state
- Rendering should not poll input
- Scanline rendering is preferred over full framebuffer use

---

## Hardware assumptions (v0.1)

Reserved pins are defined in `platform/pins.h`.

- SPI pins are fixed
- I²C pins (GP4/GP5) are reserved
- Free GPIO may be used by optional modules

Do not change pin assignments without discussion.

---

## Scope boundaries

pocketbox aims to keep its core small and reusable.

- Full games are encouraged, but large asset-heavy projects should live in their own repositories and use pocketbox as a dependency.
- Platform-specific features are welcome, but should fail gracefully or be clearly documented.
- Experimental features are encouraged; core features should justify their inclusion beyond a single game.

If you want something different, fork freely.
