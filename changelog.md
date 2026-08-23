# Changelog

Changelog for cubew, starting from its first public release (v3.47.11).

Version format: `X.Y.Z`
- X: Major (large design changes)
- Y: Minor (new features)
- Z: Patch (bug fixes, small tweaks)

---

## [3.48.0]-[3.48.11] - 2026-08 - Solver wait visualization, Auto-execute lockdown, highscore replay

### Added
- Solve (external solver) and Ask solver (in SET) now show a thin progress bar under each button, filling down as the warmup/cooldown wait elapses, and are disabled for that duration — replaces the old countdown-only toast with a clear visual sense of how much longer to wait
- While a SET → Auto-execute run or an external-solver solve is in progress, nearly every other control is now locked out (history navigation, net/rotation-pad toggles, shuffle, FACE, SET, Solve, Command Settings) to prevent a second conflicting action from being started mid-run. The net-diagram toggle and RESET stay available; pressing RESET cleanly aborts the run and resets the cube
- The history nav bar now shows real progress (`done / total`) while Auto-execute or the solver's solve is actually playing back, instead of the otherwise-meaningless "same number twice" it would show during a run
- Clearing the cube (real scramble → solve, not Auto-execute/solver-driven) now records the initial state and a CAM(θ,φ)-annotated move string alongside each Highscore entry (capped at 500 moves per entry to keep storage bounded), and a ▶ button appears next to eligible entries in the Highscore list — pressing it replays that exact solve as a Step-by-step session, camera moves included. Entries recorded before this update, or from unusually long solves past the cap, simply show no ▶ button

### Fixed
- Fixed a stopwatch label bug where the Auto-execute label could get stuck showing stale text with the wrong style after an external-solver-driven solve finished
- Fixed the Auto-execute label/nav-bar progress display flashing through an intermediate, not-very-meaningful state during the external solver's FACE-correction and API-wait phases; both now consistently reflect the actual phase (FACE correction's own progress, then the real solve's progress once the solver responds) with no in-between flicker
- Fixed SET's "Ask solver" button sometimes staying (or becoming) enabled when it shouldn't be — e.g. right after replaying a Highscore entry, or after solving the cube by hand and then closing/reopening SET — since its enabled state only accounted for the warmup/cooldown wait and not whether solving even makes sense right now
- Fixed the stopwatch text shifting vertically by a pixel or two whenever its content included an icon in a different font (e.g. switching between "Step-by-step mode" and "Playing (⏸ to stop)") — the mixed font's line-height metrics were throwing off the line's vertical centering

## [3.47.58]-[3.47.79] - 2026-08 - Auto-execute visibility, SET during Step-by-step/Exam

### Added
- The stopwatch area now shows "Auto-execute" (with the remaining move count) whenever a SET → Auto-execute run or an external-solver solve is in progress, through the pre-countdown wait, the countdown itself, and the actual playback
- Auto-execute mode and the external solver now block double-tap commands, swipe rotations, and the on-screen rotation pad while running, matching the existing protection during Autoplay — previously these could interrupt an in-progress run partway through
- SET can now be opened during a standalone (non-tutorial) Step-by-step run or Exam, showing a read-only History tab with the session's initial state and move-command strings — useful for grabbing progress mid-session. Settings and Exam tabs stay hidden in that case, since editing state or starting a new exam mid-session isn't meaningful
- SET → History's move-command strings are shown truncated (first 5 ... last 5 moves) with a move-count suffix for readability; the copy buttons always copy the full string, and are disabled when there's no history yet
- SET dialog's OK/Cancel buttons now stay visible at the bottom without needing to scroll past long move-command strings; the Command Settings dialog's footer spacing was tightened to match
- The Settings tab's icon hints (copy / rotation pad / external solver) are now shown on demand via a dedicated hint button instead of automatically flashing on first open

### Fixed
- Fixed a bug where pressing OK while SET's History tab was active silently re-applied whatever was left in the (hidden) Settings tab's fields instead of doing nothing
- Fixed a stopwatch display bug where, after an external-solver-driven solve finished, the stopwatch could get stuck showing stale "Auto-execute" text instead of resetting cleanly

## [3.47.48]-[3.47.57] - 2026-08 - Background/reload reliability, camera-follow controls

### Fixed
- The cube's 3D view could freeze after returning to the tab from a long time in the background (tab switch, other app, screen lock) — most noticeable on Android. Added WebGL context-loss recovery, plus a periodic safety check that force-resumes rendering if the normal recovery events don't fire in time (observed to be unreliable across browsers)
- The Step-by-step "actively guiding" state used to keep showing "Follow the guide" the whole way through; it now shows a distinct "Step-by-step mode" label instead

### Added
- ⏵/⏴ (forward/reverse autoplay) are no longer disabled when already at the end/start of the move history — pressing them now wraps around: ⏵ jumps to the beginning and plays through to the end, ⏴ jumps to the end and plays back to the beginning
- Standalone Step-by-step and standalone Exam mode now show a clear mode label ("Step-by-step mode" / "Exam mode") in the stopwatch area while active, temporarily replacing the personal-best-time display
- Standalone Step-by-step sequences that use CAM() now show the ⫯ pin button, letting you turn camera-follow on/off during that session (previously camera-follow was always forced on with no way to disable it, and the pin button stayed hidden)
- SET → History now offers a second, separately copyable move-command string that also includes CAM(θ,φ) markers (inserted wherever the camera view changed, plus the final view), for reproducing a free-rotation/browsing session's camera moves along with its moves
- Auto-execute mode's move-command field now accepts CAM(θ,φ) tokens (previously Step-by-step-only), animating the camera when one is encountered — pairs with the new CAM-annotated history string above
- After solving the cube, the celebration animation now returns to the home camera position before starting its horizontal spin (previously it spun from wherever the camera happened to be), and the spin now eases into a smooth stop instead of halting abruptly

## [3.47.42]-[3.47.47] - 2026-08 - Exam mode is now available outside tutorials

### Added
- The SET dialog now has a third tab, "Exam," between "Settings" and "History." Enter an initial state and a goal state (the initial-state field is pre-filled with the cube's current state) and press OK to start practicing freely toward that goal — no tutorial content required
- Reaching the goal state now triggers the celebration effect regardless of whether the exam was started from a tutorial or from the SET dialog
- RESET (⊞) now ends the current mode (with a confirmation dialog) when used during a standalone Step-by-step run or a standalone exam, instead of having no effect
- A new "Start over" button appears above the camera control buttons during a standalone exam, letting you jump back to the initial state instantly (no confirmation needed)

### Fixed
- The command-registration (⌖) and tutorial-list (📚) buttons could remain enabled during a standalone exam; they are now correctly disabled
- Toast messages from exam mode were not translated into all supported languages; they now are

## [3.47.22]-[3.47.41] - 2026-08 - SET dialog redesign

### Added
- Clear (✕) buttons on the SET dialog's text fields
- A toggle button to show/hide the on-screen rotation pad from within the SET dialog
- An "Ask external solver" button in the SET dialog: validates the entered state string, then fills the move-commands field with a solution (without applying it to the cube until you press OK)
- Brief tooltips appear on first use to introduce the new buttons

### Fixed
- The external solver could be asked to solve a state that was already solved, or that wasn't in the correct starting orientation; both are now caught and reported before any request is sent
- Long toast notifications could overflow off-screen instead of wrapping to a new line

### Changed
- Documented the difference in move-command syntax between Auto-execute and Step-by-step (Sbs) modes: `CAM()` (camera moves), `C_Xn` (aim commands), and per-face guide-arrow limiting are Step-by-step-only

## [3.47.11]-[3.47.21] - 2026-08 - Public "About" page, SVG icon system

### Added
- A new "About this app" page, available in all 9 supported languages
- Help-screen icons that previously relied on Unicode symbols (which could render inconsistently depending on the device's font) were replaced with custom SVG icons for consistent appearance across platforms
- Redesigned the help (?) button's icon

### Fixed
- A horizontal scrollbar could appear in the QR-code dialog on some browsers
- The menu (≡) button's description in the help screen no longer matched what the menu actually contains; corrected across all languages

---

*For versions prior to 3.47.11, see the private development changelog (not published here).*
