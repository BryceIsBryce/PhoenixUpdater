# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this project adheres to [Semantic Versioning](http://semver.org/).

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
- Removed the `AlwaysOnTop` game object property and related serialization/rendering behavior.
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
