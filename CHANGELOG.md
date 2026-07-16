# Changelog

## v0.1.5-preview.1 - 2026-07-15

- Fix quick loading for customer and DMZ switch panels built into the map.
- Keep loading within the focused customer or DMZ panel instead of crossing
  into an adjacent panel.
- Preserve purchased-switch targeting and avoid inactive panels.
- Add compact focus diagnostics when no switch or map panel can be resolved.
- Search for a target only after the quick-load key is pressed to reduce
  background performance impact.

Known preview limitations:

- The bottom-bar custom key hint does not appear.
- Performance while holding a module box needs broader in-game confirmation.
- Customer and DMZ switch panels built into the map are not targeted correctly
  in v0.1.4.
- Built-in customer/DMZ support needs broader in-game confirmation.

## v0.1.4-preview.1 - 2026-07-15

Initial public preview.

- Bulk-load compatible modules from a held SFP/QSFP box with a configurable
  keyboard shortcut.
- Resolve purchased switches from their bodies or individual ports, including
  when the held box blocks the direct camera ray.
- Use Data Center's current standard-SFP and 40G/QSFP compatibility rules.
- Skip occupied and incompatible ports and update the held box after transfers.
- Add compatibility diagnostics for unsuccessful attempts.
- Reduce performance impact while holding a module box.

Known preview limitations:

- The bottom-bar custom key hint does not appear.
- Performance while holding a module box needs broader in-game confirmation.
