# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this project adheres to [Semantic Versioning](http://semver.org/).

## [2.0.0-alpha.14] - 2026-08-06

### Added
- Entity pages now support checkbox-based multi-selection with batch enable, disable, clone, delete, and path-copy actions.
- Added Phoenix cursor artwork for standard, interactive, text-entry, and waiting states.
- Studio's Help menu now opens the bundled documentation, API reference, report form, update flow, community support, and application information.
- Runtime testing tools now use an ImGui interface with live performance graphs, summary cards, office-system inspection, searchable variables, detailed animatronic tracking, console filtering, and reorganized shortcut help.

### Changed
- Animatronic files are now repaired to the current pathway, night-attribute, property, and local-footstep structure when opened or restored through undo and redo.
- Playtests now enable testing tools by default and display an initial reminder for the F2 summary, F3 console, and shortcut help.
- Long-running editor actions now use a shared exception-safe waiting cursor.
- Playtests now keep the standalone console option disabled and capture runtime output in per-launch diagnostic logs instead.

### Fixed
- Fixed Animatronic editors closing Phoenix while their lazy workspace tab was still being replaced, particularly after creating the first pathway.
- Fixed project fonts with family names or OpenType extensions not resolving during runtime playtests.
- Fixed Fit Width and Fit Height backgrounds allowing a one-pixel camera drift caused by scaled-size rounding.
- Fixed Stopwatch Equals using milliseconds instead of ticks, skipping values on slow frames, and firing repeatedly between tick updates.
- Fixed splash screens remaining visible after reaching Finished when their fade animation was interrupted.
- Fixed assistance and suggestion report attachments always being named as crash reports.
- Fixed the remaining case where a newly created animatronic pathway opened from stale saved data and appeared empty or failed to open until the animatronic was saved and reopened.
- Fixed open pathway tabs retaining stale sibling names after pathways were added, renamed, or removed, which could allow conflicting names or invalid pathway targets.
- Fixed movable scene and pathway tabs displaying the wrong editor or closing the wrong tab after being reordered.
- Fixed project file selection and scene image drops failing when source files and project storage were on different Windows drives.
- Fixed delayed scene setup callbacks accessing editors or views after their tabs had already closed.
- Fixed Phoenix cursors not appearing during the initial splash screen.
- Fixed runtime ImGui tools rendering below deferred game and effect layers.

## [2.0.0-alpha.13] - 2026-08-05

### Fixed
- Fixed recurring splash-screen and Script editor crashes caused by native Qt events arriving during widget construction or teardown.
- Fixed the first pathway created for a new animatronic not being retained.
- Fixed unsupported graphics drivers and remote display sessions crashing playtests without actionable diagnostics.

## [2.0.0-alpha.12] - 2026-08-04

### Fixed
- Fixed built-in runtime images, including mask and monitor controls, being absent from packaged playtests.
- Fixed an early splash-screen mouse event that could crash Phoenix while opening a project.

## [2.0.0-alpha.11] - 2026-08-03

### Fixed
- Fixed compiled playtests failing at startup because the runtime depended on editor-only `Shared` modules for project shader migration and shader loading.
- Fixed splash-screen drag and edge-resize events accessing window state before initialization completed.
- Fixed runtime script diagnostics reaching a Script editor before its code-block view and tree were ready.
- Fixed the launcher crashing while sorting projects whose folder or `Game.json` was moved or deleted during refresh.

## [2.0.0-alpha.10] - 2026-08-01

### Added
- Playtest launches now create a per-run diagnostic log and report runtime startup errors, early exits, and nonzero exit codes inside Studio instead of failing silently.
- Scene scripts opened from menu, office, and monitor editors now offer a Phoenix-styled choice between the current workspace and the Scripts workspace, with separate remembered preferences for each scene type.
- Explorer object tooltips now identify each object's name and class.

### Changed
- Project shaders now live under `Assets/Shaders`; existing top-level `Shaders` folders are repaired automatically without overwriting conflicting files.
- Phoenix in-app prompts and editors, including scene-script creation, now use the styled Phoenix dialog system instead of native Qt dialogs.
- The Popup instance now hides its complete `Popup` group when closed rather than targeting every child object separately.
- Scene editors now offer `Hide`, `Faded`, and `Show` modes for hidden objects, defaulting to Faded.
- Animatronic Kill-path guidance now names its animatronic and only appears while that animatronic's editor tab is active.

### Fixed
- Fixed projects with complex saved workspaces crashing as Studio maximized by repairing duplicate or stale tab entries, deferring active-tab construction until the window is ready, and keeping inactive tabs lazy-loaded.
- Fixed forced workspace changes leaving the workspace selector and Studio's active-workspace state out of sync.
- Fixed Local Sound Macro level rows crashing when the Add button passed Qt's checked state into the sprite-name field.
- Fixed script block event filters accessing an editor graphics view after Qt had deleted it.

## [2.0.0-alpha.9] - 2026-07-30

### Added
- Added Phoenix shader packages (`.pxshader`) with the bundled Panorama shader, project and General Library shader folders, editable shader metadata and parameters, and a new Shader Manager under Studio tools.
- Shader Entity now exposes parameters declared by its selected shader package and applies the selected effect across the completed runtime scene.
- Added visual-script blocks to enable, disable, toggle, query, and modify Shader Entities at runtime.
- Office Properties now provides a clearable flashlight keybind and Hold or Toggle input behavior, defaulting to Left Control and allowing script-only control when cleared.
- Added script-controlled night pausing, including pause, resume, toggle, and paused-state blocks that freeze office time, power, meters, monitor movement, and animatronic simulation.
- Added horizontal, vertical, and two-axis wraparound office scrolling for authored 360-degree office perspectives.
- Added the `Power` HUD instance based on Phoenix Engine 1's power text and usage display, plus a script-controlled `Popup` instance.
- Added a runtime and editor `TextInput` object for focused keyboard entry, placeholders, length limits, submission state, and configurable input styling.
- Added Music Box path linkage to a target Status Meter so animatronic movement can be stalled by the authored music-box level.
- Added block cloning and wrapped comment message lines to script and pathway editors, with a pinned in-editor right-click guidance label.
- Added a launcher License Agreement page with its last revision date.
- Project file selectors can now browse read-only Phoenix built-in images and switch between Windows-style detail, list, and icon views through the View menu or `Ctrl+Wheel`.
- Added a playtest Starting Menu option with a dedicated Home-menu toggle and alternate-menu selector.
- Added the Phoenix Engine 1 Classic sprite collection, fonts, door animations, and music-box artwork as reusable built-in compatibility assets.
- Added compact Project/Global Font Manager and Script Library tools alongside the Shader Manager.
- Project Contents can now safely preview bounded text files when a dedicated preview is unavailable.

### Changed
- Monitor transition animations now render above ordinary scene shaders while still remaining below Shader Entities marked Always On Top.
- Office ambience now continues uninterrupted when state or perspective changes resolve to the same audio track.
- Monitor power drain can now use a configurable non-negative usage amount instead of always adding exactly one usage bar.
- Office and monitor property windows now use broader, clearer property groups without changing perspective or camera property groupings.
- Important generated scripts such as `@OfficeSystem` can no longer be renamed or deleted through Studio or scene script lists; their Enabled and Tag metadata remain editable through the Phoenix script-properties window.
- Newly generated `@OfficeSystem` scripts no longer receive a default tag.
- Text layout now uses pixel-based sizing, multiline measurement, authored horizontal and vertical alignment, and matching editor/runtime anchoring. Missing vertical alignment continues to default to Top.
- Selecting an installed font now copies its font file into the project when the project does not already contain it.
- Office-local sound macros now match the main Sound Macros workflow with compact sound rows, icon controls, ordered phone calls, visual animatronic-footstep lists, per-value resets, and Reset All.
- Project file selectors now populate large folders with lightweight native entries, preserve the rounded card/list/detail presentation, load thumbnails in responsive batches, and switch views without rescanning the directory.
- Menu, office, and monitor background fields now use the same compact image-or-animation chooser.
- Crash reports now send the complete TXT attachment as a separate final Discord message after all readable report sections.
- Opening another Studio sidebar page no longer shows an unnecessary save confirmation.
- The License Agreement page now uses the same readable panel and typography treatment as the launcher changelog.
- Added Runius to Special Thanks for originating Path Tags.

### Removed
- Removed the redundant Command Input built-in instance now that projects can use the dedicated TextInput object.

### Fixed
- Fixed mask breathing loops continuing or repeatedly restarting after the mask was removed.
- Fixed generated mask visibility logic hiding Shader Entities while the mask was worn.
- Fixed Unicode characters in project image filenames preventing those images, including menu backgrounds, from loading on Windows.
- Fixed the launcher License Agreement inheriting a hardcoded black background from the remote document instead of the active Phoenix theme.
- Fixed Shader Entity cleanup, editor performance, and scene compositing by making shader entities standalone effect markers instead of Shape objects or scene-sized editor pixmaps.
- Fixed launcher changelog callbacks accessing deleted Qt labels after navigating away.
- Fixed project creation callbacks accessing a deleted launcher page and ensured every required project folder, including Shaders, is created.
- Fixed empty animation playback and invalid frame indexes causing animation-editor crashes.
- Fixed office state selection callbacks running after their state controls were removed.
- Fixed office sound selection across different Windows drives.
- Fixed disabled scene-script actions using bright active-looking icons; protected generated-script actions are now hidden.
- Fixed script block headers showing a drag cursor without allowing the block to move.
- Fixed cloned script and pathway block trees losing their relative layout or being placed over existing blocks.
- Fixed block-editor guidance moving with the scene instead of staying pinned to the editor view.
- Fixed Output Log crashes caused by missing paths, missing log files, and locale-dependent decoding.
- Fixed splash-screen background caching crashing when the cache cannot be written, including low-disk conditions.
- Fixed runtime text objects attempting to load GPU fonts before the raylib window exists.
- Fixed non-top Shader Entities rendering above Always On Top objects; shader effects now respect the authored overlay boundary.
- Fixed office mask transition and worn-mask frames covering Always On Top objects.
- Fixed project file selector wheel scrolling becoming unusually slow after switching between list and icon views.

## [2.0.0-alpha.8] - 2026-07-01

### Added
- Added bundled `Monitor Opener` and `Clock HUD` office instances for faster monitor-button setup and a default time/night HUD.

### Changed
- Replaced the old standalone `Time Text` bundled instance with the combined `Clock HUD` setup.
- Clarified 2D scene object property display names for `Follow Camera`, `Scroll Factor`, and `Always On Top`.

### Fixed
- The expression editor no longer crashes if Qt sends events before the target editor field is fully attached.
- Studio notification timer bars now stay aligned to the bottom edge even when taller warnings or guidance popups expand.

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
