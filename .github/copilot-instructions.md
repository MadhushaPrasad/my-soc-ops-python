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

When building or modifying the UI, follow these principles to keep the app cohesive and distinctive:

- **Style system**: All styling uses custom utility classes defined in [`app/static/css/app.css`](app/static/css/app.css). Compose these utilities rather than writing one-off inline styles. Add new utilities to `app.css` when needed, following existing patterns. See [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md) for the full class reference.
- **Frontend aesthetics**: Avoid generic "AI slop" — no overused fonts (Inter, Roboto, Arial), no purple-gradient-on-white defaults, no cookie-cutter layouts. Choose distinctive typography, commit to a cohesive color palette via CSS variables, and prefer atmospheric backgrounds over plain solid fills. See [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md) for detailed guidance.
- **Motion**: Prioritize CSS-only animations. One well-orchestrated page-load reveal (using `animation-delay` staggering) delivers more delight than scattered micro-interactions.
- **Templates**: UI fragments live under [`app/templates/components/`](app/templates/components/). Keep components small and server-rendered; return partial HTML from HTMX routes rather than full-page reloads.
- **Theming**: Define colors and design tokens as CSS variables in `:root` inside `app.css`. Use `.bg-accent` and companion variables for the primary action color so theme changes propagate everywhere.

## Pitfalls And References

- Python 3.13+ is required, session state is in memory, and the session secret in [app/main.py](app/main.py) is dev-only.
- Do not use the VS Code Simple Browser. Open `http://localhost:8000` in a full browser.
- Link to existing docs instead of duplicating them: [README.md](README.md), [workshop/](workshop/), [.github/instructions/css-utilities.instructions.md](.github/instructions/css-utilities.instructions.md), [.github/instructions/frontend-design.instructions.md](.github/instructions/frontend-design.instructions.md), and [.github/instructions/general.instructions.md](.github/instructions/general.instructions.md).
