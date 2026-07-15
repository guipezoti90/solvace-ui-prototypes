# Obeya — module

Obeya board screens (feed, widgets, board update mode, comments). Currently several separate
prototype files; consolidate into one navigable `index.html` when next edited.

| Field | Value |
|---|---|
| Prototype files | see table below (5 files) |
| Figma source | add the Figma file/frame link here |
| JS prefix | `ob*` (suggested) |
| Status | Active |
| Last review | 2026-06-09 |

## Files → view / US mapping
| File | Maps to | US |
|---|---|---|
| `us-66499-feed-zoom-filtro-barra.html` | Feed: zoom + filter bar | US-66499 |
| `us-66506-widget-e-configuracao.html` | Widget + configuration | US-66506 |
| `widget-pizza-prototipo.html` | Pie/“pizza” widget prototype | (supporting) |
| `modo-atualizacao-troca-de-board.html` | Board update / switch mode | (supporting) |
| `comentarios-dropin.html` | Comments drop-in | (supporting) |

## User stories
- `user-stories/US-66499/` and `user-stories/US-66506/` started (docs to fill).

## Notes
- **Consolidation target:** one `index.html` with a single shell and one `#view-*` per screen,
  switched via `VIEWS{}` — do this the next time a screen here is worked on, not as a bulk rewrite.
- Confirm tokens vs `_shared/tokens/` during consolidation.
