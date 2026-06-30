# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this project adheres to [Semantic Versioning](http://semver.org/).

## [2.0.0-alpha.7] - 2026-06-30

### Added
- Animatronic editor warnings now flag animatronics that still do not contain any Kill path, including mask-specific guidance for the new runtime kill flow.

### Changed
- Authored `NightStart` menus now keep their project-authored visuals while still advancing into office gameplay using the special-menu runtime flow.

### Fixed
- Custom Phoenix windows can now be resized from every edge instead of only the old status-bar corner grip, and normal windows are clamped back onto the available screen area.
- Launcher project-banner cache paths are now sanitized so project titles with characters like `/` no longer crash filtered banner generation.
- Crash reports now skip empty default submissions instead of sending blank webhook messages.
- Editor sprite-door and toggle preview animations now guard against deleted `QGraphicsPixmapItem` references, preventing the recurring wrapped C/C++ deletion crash.
- Runtime text defaults now line up more closely with the editor by defaulting to Consolas and removing the oversized menu text scaling that caused cut-off menu layouts.
- Office-path animatronics no longer auto-kill the player, and jumpscare completion now waits on the configured sound or animation path more reliably.
- PE1 and editor path-type normalization now accept malformed spacing such as `Music  Box` so converted animatronic pathways load correctly again.

## [2.0.0-alpha.6] - 2026-06-25

### Fixed
- Crash report submission now sends the Discord webhook when the report window closes again, matching the intended PE1-era behavior.
- Office Properties no longer crash while building the Local Sound Macros UI for offices such as migrated FNAF 2 projects.
- Removed leftover first-run wizard code paths that were no longer part of the launcher startup flow.

## [2.0.0-alpha.5] - 2026-06-25

### Added
- First playable office, monitor, and animatronic runtime slice for Phoenix Runtime, including office scene registration, perspective/state resolution, office panning, power/time/flashlight/mask state, monitor overlay sessions, monitor camera switching, and autonomous animatronic pathway execution.
- Runtime fallback assets and builtin office instances for core PE-style gameplay widgets such as Mask, Mute Call, Battery, Toxic Bar, Time Text, Music Box, and bundled default animations like Blip, Camera, Mask, and Static.
- Office system compilation flow centered around a generated `@OfficeSystem.pxscr`, shared by the PE1 migrator, Studio playtest preflight, and runtime recompilation.
- Office-local sound macro overrides and expanded office/monitor property dialogs for authoring office ambience, calls, mask sounds, and related gameplay bindings.
- Custom workspace management in the Studio, including user-defined workspaces, improved workspace switching, and better tab routing.
- Sidebar context-menu cloning for editor entities and improved grouped-script labels that keep the script tag visible beside scene-role descriptions.
- Dedicated build/export pipeline window with explicit packaging, GitHub release, and Discord changelog steps.
- Runtime debug overlay now initializes at startup and can render performance stats with an improved in-game display.
- Runtime debug overlay now includes expanded scene state coverage, including office and animatronic runtime information.
- Visual scripting gained new input and lifecycle events (middle mouse, mouse wheel, key events, lifetime ticks, OnDraw, and OnQuit).
- Visual scripting gained new object interaction events (object hover/click and class-scoped variants).

### Changed
- PE1 migration now carries more office/monitor behavior into PE2 projects, including better office defaults, monitor conversion, generated office bindings, frame-duration conversion, and asset fallback handling.
- Playtest and runtime launch flows now treat generated office logic as a compiler-owned system step instead of scattering the behavior directly across editors and runtime entrypoints.
- Office, monitor, and animatronic editor/runtime contracts were re-audited against PE1 behavior and current PE2 authored data, with broader support for office states, monitor properties, path timing, mask flow, camera switching, and special-menu fallback handling.
- Studio workspace controls, playtest options, and project property windows were reorganized for clearer separation between engine settings, launch options, and scene-specific authored properties.
- Expression helper syntax now favors the shorter `sess.`, `game.`, and `scene.` forms and removes legacy parameter helpers.
- Script block parameter editors now support custom placeholders and required-parameter layouts for function-call blocks.
- Office editor expression hints now recognize the shorter helper syntax more reliably.
- Built-in script library examples (Audio Lure, Flashlight Disable, Golden Freddy, Hover Sound, Light Scare, Random Ads) and Premade Assets Endings have been refreshed.

### Fixed
- Office gameplay cleanup now clears lingering fullscreen effect, jumpscare, and transition animations more reliably during scene changes and overlay transitions.
- Monitor rendering, monitor transition handling, and mask visibility flow were corrected to better match intended PE office gameplay behavior.
- Animatronic runtime pacing, movement gating, and office/monitor integration received multiple fixes toward PE1-style behavior and lower-AI consistency.
- Office/monitor defaults now better match authored expectations for migrated content, including default sizing/alignment behavior and office-level background audio carryover.
- Code block parameter add button now positions correctly and reacts reliably to clicks.

## [2.0.0-alpha.4] - 2026-01-27

### Added
- Output Log now loads entries in the background with a visible loading indicator and safe cancel-on-close behavior for large logs.
- Workspace switching now prompts to save or discard unsaved tabs.
- Sidebar page switching now warns about unsaved changes before leaving the current editor.
- Playtest dialog options are now scrollable when more launch settings are available.
- Phoenix Runtime now uses the dedicated `ICON-R.ico` for its EXE icon.

### Changed
- Version checking now pulls from the raw update feed for more reliable update detection.
- New Project creation now removes template workspace layouts so every new project starts with a clean workspace.
- Animatronic editor now loads AI Level values from legacy keys more reliably and sanitizes invalid numeric values.
- Pathway editor panels now resize based on the available window height for a more consistent layout.
- Playtest now defaults “Exit Runtime On Esc” to enabled.

### Fixed
- Runtime no longer crashes on startup due to a leftover debug exception.
- Output Log copy actions now include the full message text (even when rich highlighting is used).
- Sprite animation objects now ignore empty/invalid animation names instead of failing to load.

## [2.0.0-alpha.3] - 2026-01-26

### Added
- Playtest dialog parameter system with grouped options and new runtime launch settings (target FPS control and exit-on-esc toggle) plus live command previews.
- Runtime command-line options for `--target-fps` and `--exit-on-esc`.
- Runtime now fires the `OnGameInitialize` script event on startup.
- Visual scripting now includes a new "Phoenix Tools" block category with message broadcasts and macro playback blocks.
- Office editor state environment controls for per-state background (image/animation) and music, with asset picker shortcuts.

### Changed
- State properties dialog now labels per-state audio as "Music" and uses the music picker.
- Sounds page combo boxes now preserve existing selections even if the value is not found in the current scan.
- Status bar version label now reflects the local version string (falls back to `?.?.?` when unknown).
- Runtime playtest recompile flag is now `--recompile` (reflected in the Playtest dialog).

### Removed
- Zoo Build template archived out of the built-in templates.
- Premade Assets template no longer ships a default `Workspace.json`.

### Fixed
- Color picker dialog now returns the selected color reliably and closes cleanly.
- Crash report exception text now includes richer inline context for faster debugging.
- Base page tiles no longer error when background images are missing.
- Settings initialization now tolerates missing/failed settings schemas without crashing.

## [2.0.0-alpha.2] - 2026-01-26

### Added
- Version checking now reads from a bundled `version.txt` when available and can retrieve the latest version from the update feed.
- Launcher can now start the external updater (`PhoenixEngineBootstrapper.exe`) when an update is available.

### Changed
- Update button color and click behavior now reflect whether the installed build is out of date.
- Runtime now installs the bluescreen handler as the default `sys.excepthook` for unhandled exceptions.

### Fixed
- Version comparison now guards against missing or malformed version strings to avoid startup errors.

## [2.0.0-alpha.1] - 2026-01-26

### Added
- Premade Assets template audio tracks: "ColdPresc B.wav", "In Your Office.wav", "darkness music.wav", and "jackinthebox.wav".
- Premade Assets menu scripts for Main, News, and Warning scenes.
- Build packaging now supports explicit data files and includes `Core/Scripting/ScriptBlock_API.json`.

### Changed
- Premade Assets menus reorganized into per-menu subfolders with separate `.pxmenu` and `.pxscr` files.
- Premade Assets project settings and workspace defaults now seed recent scenes and script workspace tabs.
- Premade Assets `game.json` now sets the window name to "Premade Assets" and records `EngineInfo.LastOpened`.
- Runtime now installs `PX_Bluescreen.hook` as `sys.excepthook` for runtime to display the bluescreen handler on unhandled exceptions.

### Removed
- Removed legacy Premade Assets menu files at `Scenes/Menus/Main.pxmenu` and `Scenes/Menus/Warning.pxmenu` after the menu folder restructure.

### Fixed
- Script block API documentation file is now bundled in engine builds.

## [2.0.0-alpha.0] - 2026-01-25

### Added
- Application shell with custom title bar, status bar (settings/debug/report icons + version label), and resize grip.
- Launcher with sidebar navigation for Home, New Project, Changelog, Credits, and Theme Editor.
- Splash screen with randomized backgrounds, blur treatment, progress animation, tips/facts, and fade in/out.
- Home page project hub with list/grid views, search, refresh, pinned favorites, project banners, and context actions (open, delete, set background).
- New Project flow with template cards, banner preview, project name/description/ID preview, custom banner import, and blank project option.
- Built-in templates and starter assets (Zoo Build and Premade Assets) for menus, animations, cutscenes, sounds, and images.
- Project migrator for Phoenix Engine V1/V2 and FNAF Engine V3 with options like in-place conversion, overwrite control, skip data, and resolution scaling.
- Changelog viewer with GitHub fetch (raw/API), token support, cache fallback, and status messaging.
- Theme editor with palette fields, auto shade/variant generation, and import/export of .pxtheme files.
- Multiple built-in themes (Midnight, Ember, Molten Lava, Neon Dusk, Electric Blue, Ice Bloom, Cherry Wine, Red Crimson).
- Global settings for visuals, autosave triggers, backup copies, startup behavior, error reporting, sound preview volume, animation defaults, and easter egg toggles.
- Per-project settings window for environment, animatronic behavior, caching, import behavior, audio, testing, notifications, and macros.
- Studio interface with sidebar pages for Game Info, Animatronics, Monitors, Menus, Cutscenes, Offices, Animations, Sounds, Scripts, Contents, plus Minigames and Extensions placeholders.
- Workspace system with named workspaces, persistent tabs, lazy-loaded editors, middle-click close, and last-session restore options.
- In-studio notifications with level icons and optional duplicate suppression.
- Playtest dialog to launch the bundled runtime with optional console display.
- Game Info editor with banner preview, project metadata, window name/icon/fullscreen, resolution presets/custom, and project timestamps.
- Contents browser with search/filters (case, whole word, regex), tree navigation, new folder/import/open/reveal actions, and file info previews.
- Audio preview in Contents with volume control and auto-preview option.
- Project file selector with grid view, icon caching, navigation (up/home/refresh), search options, and context actions (import/export/rename/delete/details).
- Animatronics manager to create, list, and open animatronic files with duplicate protection and enable/disable toggles.
- Animatronic editor with per-night AI attributes, dynamic AI scaling, local movement equations, jumpscare sound/animation/conclusion/consequence, and local footstep sounds.
- Visual Pathway editor with node-based paths, subpaths, drag/reorder, snapping, auto-arrange, tag validation, unreachable warnings, and per-path properties (priority, stealth, avoid-repeat, allowed nights/offices).
- Path types for animatronic logic: Camera, Door, Office, Light, Flashlight, Music Box, State, Chance, Condition, Kill, Hide, End Pathway, Restart Pathway, Jump To Path.
- Scene editors for Menus, Offices, and Monitors with canvas editing, multi-select, copy/paste/duplicate, lock/unlock, comments, grouping, layers dock, grid snapping, gridlines, zoom controls, and object metadata display.
- Menu editor environment controls for background color/image/animation, background music, menu type, and button arrow text.
- Office editor with multiple perspectives, global vs perspective objects, mask support, power settings, door/light/camera/meter controls, and aspect locking.
- Monitor editor with camera perspectives and optional office global overlay (including semitransparent mode).
- Game object palette: sprite images, rectangle shapes, text labels/button labels, status meters, sprite animations, door objects, and toggle buttons (light/door/camera/meter).
- Animation editor with timeline playback, loop, onion skinning, frame tools (add/remove/copy/paste/duplicate/move), per-frame durations, trim duplicates, reverse frames, and media import (video/GIF/image sequence).
- Animation export to MP4, animated GIF, or image sequence, plus frame-level export and clipboard tools.
- Cutscene editor with video preview, timeline scrub, playback speed, loop/mute, audio override, volume, and preview background controls.
- Scripts hub with search/filtering, global vs scene scripts, conflict detection, script creation dialog, and community script export (.pxmscr).
- Visual scripting editor with drag/drop block graph, event/action blocks, category colors, connection previews, insert-above/below/nested, auto-arrange, quick-add chips, and block documentation.
- Sound macros page with categorized sound assignments and integrated file pickers.
- Instance system to export selected objects (with category/description and optional scripts) and re-import them with parameter prompts.
- Crash handling and report template for user-facing diagnostics.

### Changed
- Version branding displayed as IDE v2.0.0 and Runtime v2.0.0 across the UI.

### Fixed
- Changelog view now falls back to cached content when offline.
- Project creation validation blocks duplicate names and missing templates.
- Banner preview falls back to a placeholder image when loading fails.
