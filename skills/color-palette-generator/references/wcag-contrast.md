# WCAG Color Contrast Reference

## Minimum Contrast Ratios
| Element | AA (Minimum) | AAA (Enhanced) |
|---------|:---:|:---:|
| Normal text (<18px) | 4.5:1 | 7:1 |
| Large text (≥18px or ≥14px bold) | 3:1 | 4.5:1 |
| UI components & graphical objects | 3:1 | 3:1 |

## Contrast Calculation
Relative luminance formula: L = 0.2126 × R + 0.7152 × G + 0.0722 × B
Contrast ratio = (L1 + 0.05) / (L2 + 0.05) where L1 > L2

## Common Safe Palettes
- Dark text on light: `#1a1a2e` on `#ffffff` (15.4:1 ✅)
- Light text on dark: `#e0e0e0` on `#1a1a2e` (12.1:1 ✅)
- Danger red on white: `#d32f2f` on `#ffffff` (5.6:1 ✅ AA)
- Link blue on white: `#1565c0` on `#ffffff` (7.1:1 ✅ AAA)
