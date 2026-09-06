---
name: image-prompts
group: Implementation
description: >-
  Write AI image prompts covering subject, lighting and composition, countering the models' bias
  toward stereotyped depictions. Use when authoring Midjourney, Flux, or DALL-E AI image prompts.
---

# image-prompts

## Core Philosophy
Authoring AI image generation prompts (Midjourney, Flux.1, DALL-E 3, Stable Diffusion) is not typing random adjectives like "hyperrealistic, 8k, award-winning trending on artstation" into a text box. Generative image models respond to precise photographic parameters, lighting physics, historical art references, spatial composition rules, and deliberate debiasing techniques. High-craft image prompts construct an exact visual scene while actively counteracting the models' algorithmic drift toward plastic, oversaturated stereotypes.

---

## 4-Step Generative Image Prompt Architecture

### Step 1: The 5-Part Architectural Prompt Anatomy
1. **The Structural Prompt Formula**:
   - `[Subject & Action]` + `[Environment & Context]` + `[Composition & Framing]` + `[Lighting & Atmosphere]` + `[Camera, Lens & Film Stock / Style Engine]`
2. **Component Breakdown**:
   - *Subject*: Specific, concrete details (clothing texture, age, posture, expression, action).
   - *Environment*: Exact time of day, architectural materials (brutalist raw concrete, wet asphalt, mahogany paneling).
   - *Composition*: Rule of thirds, low-angle hero shot, Dutch tilt, wide-angle cinematic perspective.
   - *Lighting*: Volumetric god rays, directional Rembrandt lighting, diffuse cloudy softbox, neon back-rim lighting.
   - *Camera / Medium*: 35mm photograph, Leica M11, f/1.8 aperture, shallow depth of field, Kodak Portra 400 film grain.

### Step 2: Eliminating Generative Clichés & Plastic Skin
1. **The AI Slop Kill-List for Prompts**:
   - Ban empty fluff words: `photorealistic`, `hyperrealistic`, `ultra-detailed`, `4K`, `8K`, `masterpiece`, `trending on artstation`. These words pollute the latent space with low-quality amateur renders.
2. **Enforcing Natural Texture & Imperfection**:
   - Specify real-world micro-textures to kill plastic rendering:
     - Skin: *"Subtle skin pores, natural skin texture, unretouched, faint freckles, uneven lighting."*
     - Environment: *"Dust motes in light beams, worn edges on leather notebook, subtle motion blur."*

### Step 3: Countering Stereotypical Demographic Drift
1. **Active Debiasing**:
   - Image models default to severe cultural and gender stereotypes (e.g. prompt "software engineer" produces exclusively young white or Asian men; "nurse" produces young women).
   - Explicitly specify diverse, realistic demographic descriptors, ages (e.g. "50-year-old female systems architect"), clothing (realistic workwear, not futuristic spandex), and natural working environments.

### Step 4: Technical Parameters & Engine Flags
1. **Platform-Specific Flag Tuning**:
   - *Midjourney v6*:
     - Aspect Ratios: `--ar 16:9` (landscape/hero), `--ar 1:1` (avatar), `--ar 4:5` (social portrait).
     - Stylize: `--s 50` to `--s 150` (restrained realism; default 250 is often overly cartoonish).
     - Weird & Chaos: Keep `--c 0` to `--c 10` for reproducible commercial production.
   - *Flux.1 (Dev / Schnell)*:
     - Responds best to natural language paragraphs over comma-separated tag soup.

---

## Deliverable Format: AI Image Prompt Specification (`IMAGE-PROMPTS.md`)

```markdown
# AI Image Generation Prompt Book: [Campaign / Feature]

## 1. Asset: Hero Visual for Developer Documentation
- **Target Model**: Flux.1 Dev / Midjourney v6
- **Aspect Ratio**: 16:9 (`--ar 16:9`)
- **Visual Genre**: Documentary editorial photograph

### The Master Prompt
> An authentic 35mm documentary photograph of a 42-year-old female lead infrastructure engineer debugging code late at night in a server room. She wears a navy wool sweater and glasses with thin titanium frames. Subtle facial expression of intense concentration. The background features server racks with out-of-focus amber and soft white blinking LED indicator lights. Soft rim lighting from terminal screens, moody atmospheric shadows, shallow depth of field, f/2.0 aperture. Shot on Leica M6 with Kodak Portra 400 film grain, natural skin pores and subtle shadows, zero plastic smoothing, zero neon sci-fi holograms. --ar 16:9 --s 100 --v 6.0

## 2. Negative Constraints & Exclusions
- No glowing holographic HUDs floating in air.
- No purple or magenta cyberpunk neon lighting.
- No airbrushed smooth plastic mannequin skin.
```

---

## Worked Example: Overhauling a Generic Tech Hero Visual

- **Original Prompt**: "Software engineer working on futuristic AI, hyperrealistic, 8k, glowing screens, masterpiece." -> *Produced a cartoonish neon cyborg.*
- **Refined Craft Prompt**: Specified natural documentary photography, natural daylight from a warehouse window, real mechanical keyboard, and Kodak film grain.
- **Result**: Photorealistic, credible editorial image used as the hero graphic for an enterprise Series B announcement.

---

## Verification Checklist

- [ ] Prompt follows the 5-part anatomical structure (Subject, Context, Framing, Lighting, Camera).
- [ ] Banned fluff words ("hyperrealistic", "8k", "trending on artstation") are 100% eliminated.
- [ ] Natural skin texture, grain, and physical imperfections are explicitly instructed.
- [ ] Stereotypical algorithmic drift is countered with specific demographic descriptors.
- [ ] Technical flags (`--ar`, `--s`) match target generation engine.

---

## Anti-Patterns

- **Tag Soup Prompting**: Stacking 40 disconnected keywords with commas hoping the model figures it out.
- **Cyberpunk Defaulting**: Letting models inject purple neon glows and floating binary code into serious enterprise visuals.
- **Neglecting Aspect Ratios**: Generating square images for a 16:9 website hero banner and cropping off critical subjects.
