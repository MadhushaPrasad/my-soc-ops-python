# Copilot Workspace Instructions

## Mandatory Development Checklist

- [ ] Lint: `uv run ruff check .`
- [ ] Build/boot check: `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`
- [ ] Test: `uv run pytest`

## Project Overview

Soc Ops is a small FastAPI social bingo app built with server-rendered Python, Jinja2 templates, and HTMX. Use `uv` for all project commands, and on macOS prefer `uv sync --python python3.13`.

## Architecture And Conventions

- [app/main.py](app/main.py) owns FastAPI routes, session middleware, and HTMX fragment responses.
- [app/game_logic.py](app/game_logic.py) is the home for pure game rules; [app/game_service.py](app/game_service.py) manages per-session state; [app/models.py](app/models.py) stays immutable.
- Keep interactive changes server-driven: update state in a route, then return a rendered component from [app/templates/](app/templates/), keeping templates split under [app/templates/components/](app/templates/components/).
- When behavior changes, update both [tests/test_game_logic.py](tests/test_game_logic.py) and [tests/test_api.py](tests/test_api.py) if both logic and route behavior are affected.

## Design Guide

The start screen uses a **"Midnight Bingo"** dark theme. Key design tokens are defined as CSS variables in `app/static/css/app.css` under `:root`:

| Variable | Value | Purpose |
|---|---|---|
| `--land-bg` | `#080b14` | Page background |
| `--land-gold` | `#f0c040` | Primary accent / CTA |
| `--land-coral` | `#ff6b6b` | Secondary accent |
| `--land-text` | `#e8e4dc` | Body text |
| `--land-muted` | `rgba(232,228,220,0.50)` | Subdued text |

**Typography** (loaded via Google Fonts in `base.html`):
- **Headings**: `Fraunces` — a high-contrast optical-size serif; use `font-family: 'Fraunces', serif; font-weight: 900` for display sizes.
- **Body / UI**: `Nunito` — friendly rounded sans-serif; use `font-family: 'Nunito', sans-serif; font-weight: 400|600|700`.

**Aesthetic rules for new screens**:
- Keep dark backgrounds (`var(--land-bg)` or similar deep navy).
- Use the gold accent (`var(--land-gold)`) sparingly for emphasis, CTAs, and key numbers.
- Cards / panels: `background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.10); border-radius: 0.75rem;`.
- Hover states: lift with `transform: translateY(-2px)` and a soft gold glow box-shadow.
- Entry animations: use `@keyframes content-rise` (translateY 24 → 0, opacity 0 → 1) with staggered `animation-delay` per element.
- Background depth: subtle CSS grid overlay (`rgba(255,255,255,0.03)` lines at 40 px) + blurred radial orbs.

## Pitfalls And References

- Python 3.13+ is required, session state is in memory, and the session secret in [app/main.py](app/main.py) is dev-only.
- Do not use the VS Code Simple Browser. Open `http://localhost:8000` in a full browser.
- Link to existing docs instead of duplicating them: [README.md](README.md), [workshop/](workshop/), [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md), [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md), and [.github/instructions/general.instructions.md](.github/instructions/general.instructions.md).
