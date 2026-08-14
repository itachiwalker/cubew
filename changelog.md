# Changelog

Changelog for cubew, starting from its first public release (v3.47.11).

Version format: `X.Y.Z`
- X: Major (large design changes)
- Y: Minor (new features)
- Z: Patch (bug fixes, small tweaks)

---

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
