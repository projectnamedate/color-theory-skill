# Color Wheel History & Color Models (Deep Reference)

## History of the Color Wheel

| Pioneer | Era | Contribution |
|---------|-----|-------------|
| Isaac Newton | 1666-1704 | Prism experiment; first color wheel; discovered complementary colors; published *Opticks* |
| J.W. von Goethe | 1810 | *Theory of Colours*; emotional/perceptual approach; founded color psychology |
| M.E. Chevreul | mid-1800s | Law of simultaneous contrast; influenced Impressionists |
| Albert Munsell | early 1900s | 3D color system (Hue, Value, Chroma); challenged RYB primaries as inaccurate |
| Johannes Itten | 1920s | Modern 12-step color wheel; 7 types of color contrast; Bauhaus school |
| Josef Albers | 1963 | *Interaction of Color*; color relativity and context-dependence |
| Pantone | 1960s | Standardized color matching across industries |

## Color Models Detail

### RYB (Traditional/Artistic)
- Primaries: Red, Yellow, Blue
- Secondaries: Orange, Green, Purple
- Tertiaries: Red-Orange, Yellow-Orange, Yellow-Green, Blue-Green, Blue-Purple, Red-Purple
- Now considered scientifically inaccurate but still useful for artistic intuition

### RGB (Additive/Light - screens)
- Primaries: Red, Green, Blue
- Secondaries: Cyan, Magenta, Yellow
- All primaries combined = White; absence = Black
- Standard encoding: 0-255 per channel (24-bit = 16,777,216 colors)

### CMY/CMYK (Subtractive/Print)
- Primaries: Cyan, Magenta, Yellow (+K for Black)
- Secondaries: Red, Green, Blue
- All primaries combined = Black (theoretically); K added for true dense black
- Device-dependent; requires ICC profiles for accurate conversion

## Color Mixing

### Additive Mixing (Light / RGB)
Combines light emissions. More color = closer to white.

| Mix | Result |
|-----|--------|
| Red + Green | Yellow |
| Red + Blue | Magenta |
| Green + Blue | Cyan |
| Red + Green + Blue | White |
| No light | Black |

### Subtractive Mixing (Pigment / CMYK)
Combines inks/pigments that absorb wavelengths. More color = closer to black.

| Mix | Result |
|-----|--------|
| Cyan + Magenta | Blue |
| Cyan + Yellow | Green |
| Magenta + Yellow | Red |
| Cyan + Magenta + Yellow | Black (muddy; hence K plate) |

### Optical/Partitive Mixing
Tiny adjacent color areas blend perceptually at a distance. More luminous than physical mixing.
- Pointillism (Seurat), halftone printing, woven textiles, LED sub-pixels

## Color Spaces (Extended)

### HSL vs HSV
- **HSL:** Purest color at L=50%; both L=0% (black) and L=100% (white) are achromatic. Common in CSS `hsl()`.
- **HSV/HSB:** Purest color at S=100%, V=100%; V=0% is always black. Common in image editors (Photoshop).
- **Critical limitation of both:** Not perceptually uniform. Yellow at L=50% appears far lighter than blue at L=50%.

### OKLCH (Recommended for Modern Design)

| Dimension | Range | Description |
|-----------|-------|-------------|
| **L** (Lightness) | 0-1 | Perceptually uniform: L=0.6 looks equally bright for ANY hue |
| **C** (Chroma) | 0-~0.37 | Absolute colorfulness (not relative like HSL saturation) |
| **H** (Hue) | 0-360 | Hue angle: ~20=red, ~90=yellow, ~140=green, ~220=blue, ~320=purple |

Why OKLCH over HSL:
- No hue shift when adjusting lightness or chroma
- Perceptually uniform lightness (reliable contrast predictions)
- Can encode Display P3 and wider gamuts
- Predictable accessibility: all colors with L >= 0.87 have good contrast with black text
- CSS: `oklch(0.7 0.15 250)` or `oklch(70% 0.15 250)`

### OKLAB
- Cartesian form of OKLCH: L (lightness), a (green-red), b (blue-yellow)
- Best for gradient interpolation - no hue shifts, no muddy midpoints
- CSS: `linear-gradient(in oklab, blue, yellow)`

### Color Gamut

| Gamut | Coverage | Use | CSS |
|-------|----------|-----|-----|
| **sRGB** | ~35% of visible spectrum | Web standard since 1996 | Default for hex/rgb |
| **Display P3** | ~25-30% wider than sRGB | Modern Apple/OLED screens | `color(display-p3 r g b)` |
| **Adobe RGB** | Wider than sRGB (cyan-green) | Photography, print | Not for web |
| **Rec. 2020** | ~75% of visible | HDR video/TV | Emerging |
