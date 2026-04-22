# Connecting Models to Data: Booth Demo

Interactive HTML experience for Red Hat Summit showcasing the **Connecting Models to Data** pillar of Red Hat AI.

## What It Does

A pipeline animation walks through the FedAura loan-processing story across seven stages, from data ingestion to production scaling. Three **anchor stages** (AutoML, AutoRAG, Eval Hub) open a detail panel with component info and inline video demos. The remaining stages show lighter inline descriptions with optional demo links.

### The Pipeline

| Stage | Component | Role |
|-------|-----------|------|
| Ingest | Data Processing (Docling) | Non-anchor |
| Train | Training Hub (OpenShift AI) | Non-anchor |
| Decide | **AutoML** | Anchor |
| Explain | **AutoRAG** | Anchor |
| Test | SDG Hub | Non-anchor |
| Validate | **Eval Hub** | Anchor |
| Refine | ITS Hub | Non-anchor |

## How to Use

Open `index.html` in a browser. That's it: no build step, no server required.

### Three Modes

- **Attractor:** Auto-cycles through stages (interval configurable in Settings, default 7 seconds). Leave it running at the booth.
- **Guided:** Click anchor stages to read the summary, then use the **See it in action →** CTA to open the detail panel. Narrate while the video plays.
- **Self-service:** Share the link. Visitors explore at their own pace.

### Controls

| Input | Action |
|-------|--------|
| Click stage | Select stage (pauses auto-cycle) |
| Click "See it in action →" | Open detail panel (anchor stages only) |
| Click outside panel | Close panel |
| Arrow keys | Navigate stages |
| Enter | Open panel for current anchor |
| Escape | Close panel or settings |
| Spacebar | Pause/resume auto-cycling |
| Header gear icon | Open Settings (stage time, text size — default 160%) |
| Header theme icon | Cycle dark / light / high contrast |
| Drag / double-click text | Select text on the storyline, detail card, or side panel (other chrome is unselectable so click-through stays clean) |

## File Structure

```
index.html          # The entire experience: HTML, CSS, JS in one file
videos/
  automl.mp4        # AutoML demo video
  autorag.mp4       # AutoRAG demo video
  evalhub.mp4       # Eval Hub demo video
  sdg.mp4           # SDG Hub demo video
  its.mp4           # ITS Hub demo video
```

## Sources

- **Process View**: [booth2.html](https://franksworld.com/labs/redhat/booth2.html) by Frank La Vigne
- **Component View**: [CMD](https://github.com/lukeinglis/CMD) by Luke Inglis

## Tech Stack

- Vanilla HTML, CSS, JavaScript: no framework, no build step
- Google Fonts (Syne + DM Sans)
