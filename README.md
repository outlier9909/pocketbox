# pocketbox

**pocketbox** is a tiny, feel-first game runtime for cheap microcontroller hardware.

It is designed for:
- RP2040 (Raspberry Pi Pico and compatibles)
- small SPI TFT displays (e.g. ST7735 128×160)
- physical controls (buttons, rotary encoders)
- battery-powered, handheld, junk-drawer builds

pocketbox is **not** a retro emulator, a sprite engine, or a UI framework.
It is a low-level runtime for experiments where *motion, timing, and physical response* matter more than pixels.

If you’ve ever had a pile of $3 screens and no good reason to use them — this is that reason.

---

## What pocketbox is

- A **scanline-driven render loop**
- A **deterministic timebase**
- A **state-first simulation model**
- A **hardware-respecting design**
- A foundation for multiple small games on the same cheap platform

pocketbox assumes constraints and leans into them.

---

## What pocketbox is not

- Not sprite-first (sprites are optional tools, not the worldview)
- Not tilemap-first
- Not menu-heavy
- Not an emulator
- Not “Arduino demo code”

If you want instant gratification, there are better tools.
If you want something that *feels alive on bad hardware*, welcome.

---

## Supported hardware (v0.1)

**Baseline platform**
- RP2040 (Raspberry Pi Pico or clone)
- ST7735 128×160 SPI TFT
- 6 momentary buttons
- 2 rotary encoders
- Li-Po battery + TP4056 (with protection)
- On/off load switch

**Optional modules**
- RGB LED(s)
- Vibration motor
- I²C peripherals (IMU, etc.)

All optional hardware uses reserved GPIO and is safe to omit.

---

## Philosophy

pocketbox treats hardware limitations as an aesthetic constraint, not a flaw.

- Rendering is scanline-based, not framebuffer-heavy
- Motion is continuous and damped, not stepped
- Input feeds simulation, not rendering
- Rendering expresses state — it does not own logic

Games built on pocketbox should feel:
- physical
- deliberate
- slightly uncanny

---

## Project status

This project is early, experimental, and intentionally small.

The goal is not mass adoption.
The goal is **clarity, feel, and reuse**.

If you build something strange with it, that’s a success.

---

## License

MIT (for now). Build freely.
