-------------------------------------------------------------------------------
# DaVinci Resolve 16

**Source**: [Learning DaVinci Resolve 16 (LinkedIn Learning)](https://www.linkedin.com/learning/learning-davinci-resolve-16) by Patrick Inhofer

<!-- MarkdownTOC -->

- [1. Introduction](#1-introduction)
    - [1.1. DaVinci Resolve vs DaVinci Resolve Studio](#11-davinci-resolve-vs-davinci-resolve-studio)
    - [1.2. Project manager](#12-project-manager)
    - [1.3. Overview](#13-overview)
    - [1.4. Global preferences](#14-global-preferences)
    - [1.5. Keyboard shortcuts](#15-keyboard-shortcuts)
- [2. Media page](#2-media-page)
    - [2.1. Project frame rate](#21-project-frame-rate)
    - [2.2. Importing media](#22-importing-media)
    - [2.3. Organizing media](#23-organizing-media)
    - [2.4. Reviewing and marking clips](#24-reviewing-and-marking-clips)
    - [2.5. Metadata and keywords](#25-metadata-and-keywords)
    - [2.6. Smart bins](#26-smart-bins)
    - [2.7. Power bins](#27-power-bins)
- [3. Cut page](#3-cut-page)
    - [3.1. Overview](#31-overview)
    - [3.2. Building up a timeline](#32-building-up-a-timeline)
    - [3.3. Viewer features](#33-viewer-features)
    - [3.4. Basic editing](#34-basic-editing)
    - [3.5. Edit tools](#35-edit-tools)
- [4. Edit page](#4-edit-page)
    - [4.1. Viewers](#41-viewers)
    - [4.2. Timeline](#42-timeline)
    - [4.3. Editing](#43-editing)
    - [4.4. Inspector](#44-inspector)
    - [4.5. Keyframing](#45-keyframing)
    - [4.6. Speed ramping](#46-speed-ramping)
- [5. Color Page](#5-color-page)
    - [5.1. Overview](#51-overview)
    - [5.2. Color wheels \(overview\)](#52-color-wheels-overview)
    - [5.3. Color wheels \(workflow\)](#53-color-wheels-workflow)
    - [5.4. Waveforms](#54-waveforms)
    - [5.5. Automatic color correction](#55-automatic-color-correction)
    - [5.6. Copy correction settings](#56-copy-correction-settings)
    - [5.7. Node-based color correction](#57-node-based-color-correction)
    - [5.8. Gallery](#58-gallery)
    - [5.9. Curves](#59-curves)
    - [5.10. Versus curves](#510-versus-curves)
    - [5.11. HSL keyer](#511-hsl-keyer)
    - [5.12. Power windows](#512-power-windows)
    - [5.13. OpenFX](#513-openfx)
- [6. Visual effects and audio mixing](#6-visual-effects-and-audio-mixing)
    - [6.1. Fusion title generator](#61-fusion-title-generator)
    - [6.2. Fusion page](#62-fusion-page)
    - [6.3. Fairlight page](#63-fairlight-page)
    - [6.4. Audio editing and mixing](#64-audio-editing-and-mixing)
- [7. Rendering and delivery](#7-rendering-and-delivery)
    - [7.1 Deliver page](#71-deliver-page)
    - [7.2. Additional resources](#72-additional-resources)

<!-- /MarkdownTOC -->

-------------------------------------------------------------------------------
## 1. Introduction

### 1.1. DaVinci Resolve vs DaVinci Resolve Studio

Although *DaVinci Resolve* (free) for the most part is the same software as *DaVinci Resolve Studio* (paid), it has some limitations:

1. **Noise reduction**
    - *Resolve Studio* has integrated noise reduction
    - can buy third party noise reduction plugins, but none renders faster than the native tool

2. **Rendering restrictions**
    - only UHD frame size or smaller
    - no deinterlacing
    - no `3:2` pulldown on rendering
    - no face detection
    - no HDR tools (and no Dolby Vision)
    - using no more than one graphics card to accelerate real time playback and rendering (possible on Mac)

3. **ResolveFX plugins**
    - there is a number of useful plugins available for *Resolve Studio* (e.g. *film grain*, *lens flare*, *color stabilizer*, *object removal*, *face refinement*)
    - these plugins can be bought separately, but it may be cheaper to purchase *Resolve Studio* instead
    - some third party plugins are *Resolve Studio* only

4. **Collaborative workflow**
    - *Resolve Studio* allows for local real-time collaboration for users working on the same project
    - won't work on Mac app store version of *Resolve Studio*

5. **Remote grading**
    - *Resolve Studio* allows for remote real-time collaboration for users working on the same project

Projects created by both versions of *DaVinci Resolve* are identical and can be freely swaped between the two installs.


### 1.2. Project manager

When you launch Resolve, the first place it takes you is the **Project Manager**. From here you can open, import, export *projects*, and manage *databases* (locations where all the projects and archives are stored). The active project is highlighted with orange border.

<p style="text-align:center;"><img src="data/project manager.png" width="600" title="project manager"></p>

*DaVince Resolve* projects are stored as `.drp` files. They don't include media files, which are stored separately inside `.dra` archives (folders). *DaVinci Resolve* archive includes *audio consolidate*, *graphics*, *music*, *screen shot consolidated*, *video transcoded*, and *VO* directories.

1. **Importing projects**
    - `Import Project...` option in *Project Manager*
    - when `.drp` project is imported, all media files need to be relinked: *Media Page* → select required media files (or folders) → `Relink Selected Clips` (or `Relink Clips For Selected Bins`)
    - sometimes *DaVinci Resolve* will propose to perform a deep search (if the folder structure isn't what it expects)

2. **Restoring archives**
    - `Restore Project Archive...` option in *Project Manager*
    - when `.dra` folder is restored, all media files from a project will be relinked automatically

3. **Exporting projects and archives**
    - `Export Project...` and `Export Project Archive...` options in *Project Manager*
    - there is an option for `Export Project with Stills and LUTs...`, if you've been using lookup tables or saving stills in the *Color Page*


### 1.3. Overview

The workflow in *DaVinci Resolve* is organized with the help of different *pages*:

<p style="text-align:center;"><img src="data/pages strip.png" width="700" title="pages strip"></p>

1. **Media**
    - place for importing media files into a project
    - load media files into a current project by moving them from `Media Storage` (upper half; all media files on a computer) to `Media Pool` (bottom half; footage that can be used in a current project)
    - clips can be previewed in the viewer (by hovering over a thumbnail)
    - `Audio` and `Metadata` palettes for more info about media files (top right)

2. **Cut**
    - place for building a project timeline (supplements *Edit Page*)
    - `Media Pool` or other palettes (upper left)
    - *top timeline*:
        - always zoomed out at 100% (for quick navigation)
        - when you click and drag the ruler, you're moving the playhead around
    - *bottom timeline*:
        - always zoomed in 
        - when you click and drag the ruler, you're sliding the timeline around (the playhead is locked to the center)

3. **Edit**
    - place for fine tune edits; more traditional timeline, i.e. easy to get to key frames and adjust individual audio channels
    - `Media Pool` on the left side (can be resized)
    - *dual viewer*:
        - clips appear in the *left side viewer* when you hover over thumbnails (double-click to put a clip in the viewer permanently)
        - *right side viewer* shows a video from a timeline
    - additional editing tools are available in the `Inspector` (top right)

4. **Fusion**
    - place for visual effects

5. **Color**
    - place for color grading and color correction
    - two independent timelines: *thumbnail timeline* and *mini timeline*
    - clip highlighted with orange border is showed in the viewer
    - *color correction tools* at the bottom, and `Node Tree` in the upper right (a single node contains all current color corrections)

6. **Fairlight**
    - place for audio mixing

7. **Deliver**
    - place for rendering projects


### 1.4. Global preferences

Global preferences are settings that will persist between projects and databases.

- **System preferences**
    - Memory and GPU
    - Media Storage (fastest storage device should be put first)
    - Decode Options
    - Video and Audio I/O
    - Audio Plugins
    - Control Panels
    - General
    - Internet Accounts
    - Speaker Setup

- **User preferences**
    - UI settings
    - Project Save and Load
    - Editing
    - Color
    - Fairlight
    - Playback Settings
    - Control Panels
    - Metadata

There are also some additional preferences and settings:

- for full screen view: `Workspace` → `Full Screen Window`
- reset UI: `Workspace` → `Reset UI layout`
- UI presets: `Workspace` → `Layout Presets` → `Save Layout as Preset...`/`Import Layout as Preset...`
- to minimize *Pages Strip*: RMB → `Show Icons Only`


### 1.5. Keyboard shortcuts

Can create, export, and import keyboard shortcuts layouts.

#### General

| Shortcut                        | Action             |
| ------------------------------- | ------------------ |
| <kbd>Shift</kbd> + <kbd>1</kbd> | Project Manager    |
| <kbd>Ctrl</kbd> + <kbd>,</kbd>  | Global Preferences |

#### Markers

| Shortcut                                       | Action                                                |
| ---------------------------------------------- | ----------------------------------------------------- |
| <kbd>I</kbd> / <kbd>O</kbd>                    | set in and out points                                 |
| <kbd>M</kbd>                                   | set a marker                                          |
| <kbd>M</kbd>, <kbd>M</kbd>                     | marker options                                        |
| <kbd>Shift</kbd> + <kbd>↑</kbd> / <kbd>↓</kbd> | go to the next/previous marker                        |
| <kbd>X</kbd>                                   | set in and out points (in the timeline)               |
| <kbd>Alt</kbd> + <kbd>X</kbd>                  | remove in and out points (in the timeline)            |
| <kbd>Alt</kbd> + <kbd>B</kbd>                  | create a subclip (from a clip with in and out points) |

#### Viewer

| Shortcut                                  | Action                                     |
| ----------------------------------------- | ------------------------------------------ |
| <kbd>J</kbd> / <kbd>J</kbd>, <kbd>J</kbd> | play backward (normal/double speed)        |
| <kbd>K</kbd>                              | pause                                      |
| <kbd>L</kbd> / <kbd>L</kbd>, <kbd>L</kbd> | play forward (normal/double speed)         |
| <kbd>K</kbd> + <kbd>J</kbd>               | go one frame backward                      |
| <kbd>K</kbd> + <kbd>L</kbd>               | go one frame forward                       |
| <kbd>/</kbd>                              | go back a couple seconds and play          |
| <kbd>Q</kbd>                              | switch between source and timeline viewers |
| <kbd>P</kbd>                              | cinema viewer                              |
| <kbd>Alt</kbd> + <kbd>F</kbd>             | enhanced viewer                            |
| <kbd>Shift</kbd> + <kbd>F</kbd>           | full page viewer                           |

#### Timeline

| Shortcut                                                     | Action                                                   |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| <kbd>↑</kbd> / <kbd>↓</kbd>                                  | go to the next/previous edit                             |
| <kbd>Ctrl</kbd> + <kbd>=</kbd>/<kbd>-</kbd>                  | zoom in/out                                              |
| <kbd>Shift</kbd> + <kbd>Z</kbd>                              | zoom to the entire timeline view (press again to unzoom) |
| <kbd>Backspace</kbd>                                         | remove selected clips or area                            |
| <kbd>Delete</kbd>                                            | remove selected clips or area (with empty gaps)          |
| <kbd>E</kbd>                                                 | extend selected edit point to the current time indicator |
| <kbd>A</kbd>                                                 | selection mode                                           |
| <kbd>T</kbd>                                                 | trim mode                                                |
| <kbd>F9</kbd>/<kbd>F10</kbd>/<kbd>F11</kbd>                  | insert/overwrite/replace clip                            |
| <kbd>F12</kbd>/<kbd>Shift</kbd> + <kbd>F12</kbd>             | place on top/append to end                               |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>,</kbd>/<kbd>.</kbd> | swap selected clip with the previous/next one            |
| <kbd>Ctrl</kbd> + <kbd>C</kbd>                               | copy Inspector attributes from a clip                    |
| <kbd>Alt</kbd> + <kbd>V</kbd>                                | paste Inspector attributes to a clip                     |

#### Color correction

| Shortcut                                          | Action                                          |
| ------------------------------------------------- | ----------------------------------------------- |
| <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>W</kbd> | show/hide waveforms window                      |
| <kbd>Shift</kbd> + <kbd>H</kbd>                   | toggle on/off highlights mode (viewer)          |
| <kbd>Shift</kbd> + <kbd>~</kbd>                   | toggle on/off screen widget (viewer)            |
| <kbd>Alt</kbd> + <kbd>S</kbd>                     | add a node to the chain                         |
| <kbd>E</kbd>                                      | extract the node from the chain                 |
| <kbd>Ctrl</kbd> + <kbd>C</kbd>                    | copy color corrections from a node              |
| <kbd>Ctrl</kbd> + <kbd>V</kbd>                    | paste color corrections to a node               |
| <kbd>Alt</kbd> + <kbd>V</kbd>                     | paste color corrections to a node (choose what) |


-------------------------------------------------------------------------------
## 2. Media page

### 2.1. Project frame rate

Before you import any clips into a project, you need to set the *project frame rate* in `Project Settings` (gear icon in the bottom right corner) → `Master Settings`, because **once set it cannot be changed later.**

<p style="text-align:center;"><img src="data/project frame rate.png" width="350" title="project frame rate"></p>

- if there's a mismatch between the very first clip dragged into the `Media Pool` and the project frame rate, you'll see a dialogue box, which will ask if you want to change the current project frame rate
- in addition to the *timeline frame rate* there is a *video monitoring frame rate*, which can be configured independently (so you can monitor you footage externally at another frame rate)
- can render a project at any frame rate, but it's better if the output frame rate matches your project frame rate


### 2.2. Importing media

There are several ways of adding media to the `Media Pool`:

1. **Windows Explorer**
    - drag and drop individual clips or whole folders
    - to maintain the folder structure, drag it to the bins sidebar

2. **Media Storage**
    - drag and drop individual clips or whole folders (or RMB on clips in the sidebar of the `Media Storage` and `Add Folder and Subfolders into Media Pool`)
    - drag clips directly to the `Media Pool` or to the bins sidebar

<p style="text-align:center;"><img src="data/media storage.png" width="650" title="media storage"></p>


### 2.3. Organizing media

It's convenient to store different types of imported media in separate *bins* (e.g. for audio, video, and graphics)

- can sort (RMB on *Master Folder* and `Sort By`) and color tag bins (RMB on a bin and `Color Tag`)
- can choose poster frames for clips (RMB on a frame and `Set Poster Frame`), which can be useful for clips with graphics
- there are different bin view options (top right of the `Media Pool`)
- can also have multiple bins open at the same time (RMB on a bin and `Open As New Window`)


### 2.4. Reviewing and marking clips

#### Reviewing clips

When you hover over a clip in the `Media Pool`, it appears in the viewer. To make this behaviour less distracting you can:

- turn off the audio button underneath the viewer
- turn off live scrub (`...` on the top right of the viewer → turn off `Live Media Preview`)

#### Marking clips

Often before editing it's useful to mark the parts of a footage that are going to be used. *Inpoints*, *outpoints* and *markers* are used for that (set with shortcuts).

- *inpoints* and *outpoints* are used to create subclips in the **Edit Page** (RMB on a clip and `Create Subclip`)
- *markers* can have names, notes, keywords and color tags
- can create *duration markers* (with <kbd>alt</kbd> + LMB drag from a marker), which can be used for setting in and out points for a clip (RMB and `Set In and Out from Duration Marker`)

<p style="text-align:center;"><img src="data/media - markers.png" width="450" title="markers"></p>


### 2.5. Metadata and keywords

*DaVinci Resolve* allows to store a lot of metadata arrect media.
), but it does be changed (e.g. frame rate

- there are many useful fields that exist only within *DaVince Resolve* (e.g. keywords, people)
- *DaVince Resolve* has a big list of predetermined *keywords*, but it can be modified (`Workspace` → `Keyword Dictionary...`)
- another useful metadata category is *People*, it's populated automatically with the help of face recognition algorithms (available only in *Resolve Studio*)


### 2.6. Smart bins

*Smart Bins* are special kind of bins that use metadata to automatically populate themselves with footage.

- to show/hide: `View` → `Show Smart Bins`
- to add a *smart bin*: RMB on the lower part of a bin view, `Add Smart Bin...` and choose the metadata you want to use to populate the bin
- *Smart Bins* allow for a single clip to appear in multiple bins, and those bins update in real time as new clips are added and tagged with metadata
- *Resolve Studio* has a face detection feature, which allows to fill smart bins with clips based on the people detected in them (RMB on selected clips and `Analyze Clips for People`); after people have been detected you can manually refine the results


### 2.7. Power bins

Sometimes you have media files that you reuse across multiple projects (e.g. show openers and lower thirds). Instead of importing them into every project, you can create a *power bin* for them (a bin that is available for every project within a particular database).

- to show/hide: `View` → `Show Power Bins`
- *Power Bins* exist within one database, but across all projects in that database

<p style="text-align:center;"><img src="data/media - bins.png" width="550" title="media bins"></p>


-------------------------------------------------------------------------------
## 3. Cut page

### 3.1. Overview

The *Cut Page* is designed to streamline the editing process. The main goal is to get to the rough cut of the project as soon as possible.

- *Cut Page* gives an instant access to some project settings (top right of the viewer): *frame size*, *color correction bypass*, *mute audio*, and *quick export* button.
- double-click on a clip from the `Media Pool` (top left) to put it into the viewer, and drag it down to put it into a project timeline
- there are two timelines in the *Cut Page*:
    - *top timeline*
        - always zoomed out at 100% (for quick navigation)
        - when you drag the ruler, you're moving the playhead around
    - *bottom timeline*
        - always zoomed in
        - when you drag the ruler, you're sliding the timeline around, but this behavior can be changed with `Free/Lock Playhead` button (to the left of the top timeline)
    <p style="text-align:center;"><img src="data/cut - timelines.png" width="700" title="timelines"></p>
- the first clip dragged into a timeline starts at `01:00:00:00` by default (can be changed by modifying the timeline start time code in the *Edit Page*)
- when new clips are added, they automatically snap to the end of a timeline, i.e. not allowing to create empty gaps (unlike in the *Edit Page*)


### 3.2. Building up a timeline

- main goal is to quickly build up a timeline and an initial rough cut, while concentrating on narration instead of editing
- use the base video track for narration and determining the pace and place additional clips above it for fine edits, cuts, and transitions
- when using the *Cut Page*, *Resolve* manages all the audio tracks automatically


### 3.3. Viewer features

- jog control `< o >` allow to quickly move through a timeline
- can use *cinema viewer* (full screen view, see shortcuts)
- three viewer modes (top left corner of the viewer; can switch between them with a shortcut):
    1. **Source Clip**
        - showing a selected clip from the `Media Pool`
        - can hover over clips in the `Media Pool` and they will appear in the viewer (can also set in and out point while scrubing)
    2. **Source Tape**
        - showing all the clips from the `Media Pool` in the chronological order
        - can set in and out points for individual clips
    3. **Timeline**
        - showing a timeline
        - can still place markers and in and out points (but for the whole timeline instead of individual clips)
    <p style="text-align:center;"><img src="data/cut - viewer.png" width="600" title="cut page viewer"></p>
- to speed up the process of reviewing the footage there is a `Fast Review` option (bottom left corner of the viewer): when playing clips it speeds up on longer takes and slows down a little on shorter takes.
    <p style="text-align:center;"><img src="data/cut - fast review.png" width="500" title="fast review"></p>


### 3.4. Basic editing

Despite being designed for quick editing, *Cut Page* offers many editing tools:

- quickly *navigate* between edits with shortcuts; can also set *markers* and *in* and *out points* (use shortcuts)
- can *extend* and *crop* clips (drag the edge)
    <p style="text-align:center;"><img src="data/cut - extend clip.png" width="300" title="extend clips"></p>
- can use *trim* and *ripple* tools to adjust clips to each other (remember that in the *Cut Page* *Resolve* will try to keep everything in sync and won't allow empty gaps)
    <p style="text-align:center;"><img src="data/cut - trim edit.png" width="650" title="trim and ripple edit"></p>


### 3.5. Edit tools

*Cut Page* edit tools (above the top timeline):

<p style="text-align:center;"><img src="data/cut - edit tools.png" width="350" title="edit tools"></p>

- `Smart Insert`

    Drop selected clip to the closest edit point to the current time indicator (highlighted with `ˇ` symbol in the bottom timeline), and push other clips back if needed.

    <p style="text-align:center;"><img src="data/cut - smart insert.png" width="300" title="smart insert"></p>

- `Append`

    Drop selected clip to the end of a timeline.

- `Close Up`

    Create close up (change parameters through `Tools` button in the viewer).

    - `Transform`

        Blow up the shot (can adjust scale, position, rotation, etc.).

    <p style="text-align:center;"><img src="data/cut - close up.png" width="650" title="close up"></p>

    - `Dynamic Zoom`

        Create dynamic zoom. Green frame for start shot, red frame for end shot.

    <p style="text-align:center;"><img src="data/cut - dynamic zoom.png" width="650" title="dynamic zoom"></p>

- `Place on Top`

    Drop selected clip at the top layer of a timeline.

- `Dissolve` (uses smart tool)

    Create dissolve between two clips (similar to crossfade between audio clips).

    <p style="text-align:center;"><img src="data/cut - dissolve.png" width="450" title="dissolve"></p>

- `Cut` (uses smart tool)

    Turn dissolve back into a cut.


-------------------------------------------------------------------------------
## 4. Edit page

### 4.1. Viewers

- dual viewer setup by default with the *source* and *timeline viewers* (toggle between them with a shortcut), but can change to a single viewer setup (top right corner of the *timeline viewer*)
    <p style="text-align:center;"><img src="data/edit - dual viewer.png" width="800" title="dual viewer"></p>
- `Match Frame` (bottom right corner of the *timeline viewer*) to put a clip from a timeline to the *source viewer*
- same `Tools` as in the *Cut Page* (bottom left corner of the *timeline viewer*)
- can jump to a specific time of a clip in the *source viewer* with shortcuts, e.g. `1 00 00 Enter` will jump to one minute mark
- can show audio waveforms in the *source viewer* (`...` at the top right corner), this can help to set in and out points
- audio clips have a dual waveform view in the *source viewer* (zoomed in and full length)
    <p style="text-align:center;"><img src="data/edit - waveform.png" width="400" title="audio clips"></p>
- can change the amount of screen space occupied by the `Media Pool` (top left corner)
    <p style="text-align:center;"><img src="data/edit - media pool.png" width="400" title="media pool"></p>


### 4.2. Timeline

*Edit Page* uses a single timeline.

- use shortcuts to zoom and navigate; adjust audio and video tracks height and appearance with `Timeline View Options` (top left corner of the timeline)
    <p style="text-align:center;"><img src="data/edit - timeline view options.png" width="220" title="timeline view options"></p>
- can drag clips freely, i.e. *Edit Page* allows empty gaps 
- can move video clips independently of audio (when `Linked Selection` is off)
    <p style="text-align:center;"><img src="data/edit - linked selection.png" width="400" title="linked selection"></p>
- adjust clips to each other by moving them using shortcuts, e.g. `+22 Enter` will move selected clip 22 frames forward (see the top right corner of the *timeline viewer*)
- control audio for tracks with `Mixer` (button above the *timeline viewer*)
    <p style="text-align:center;"><img src="data/edit - mixer.png" width="400" title="mixer"></p>
- control audio for individual clips with `Inspector` (button above the *timeline viewer*)
    <p style="text-align:center;"><img src="data/edit - audio inspector.png" width="350" title="audio inspector"></p>


### 4.3. Editing

*Edit Page* provides more advanced editing tools comparing to the *Cut Page*.

- can *extend*, *crop*, *drag*, *adjust* and *trim* clips (`Selection Mode`, `Trim Edit Mode`, and other edit modes)
    <p style="text-align:center;"><img src="data/edit - edit modes.png" width="150" title="edit modes"></p>
- can *slip edit* (select top part of a clip and drag), i.e. the duration of a clip and in and out points are unchanged, the content of a clip is changing
    <p style="text-align:center;"><img src="data/edit - slip edit.png" width="300" title="slip edit"></p>
- can *slice edit* (select bottom part of a clip and drag), i.e. the content of a clip and its duration stay the same, in and out points are moving
    <p style="text-align:center;"><img src="data/edit - slice edit.png" width="300" title="slice edit"></p>
- drag a clip from the *source viewer* to the *timeline viewer* to see different options for inserting a clip into a timeline: `Insert`, `Overwrite`, `Replace`, `Fit to Fill`, `Place on Top`, `Append at End`, and `Ripple Overwrite` (can also use shortcuts)
    <p style="text-align:center;"><img src="data/edit - insert tools.png" width="400" title="insert clips"></p>
- can *swap* clips with each other (see shortcuts)
- *track selectors* (orange box around the track) determine the tracks where new clips are inserted
- turn off the *auto selector* for a particular track to ignore the edits for clips on it (e.g. when swaping clips and triming)
    <p style="text-align:center;"><img src="data/edit - autoselector.png" width="350" title="autoselector"></p>


### 4.4. Inspector

- provides same video editing tools as `Tools` button from the *Cut Page* (`Transform`, `Dynamic Zoom`, `Stabilization`, etc.)
    <p style="text-align:center;"><img src="data/edit - inspector.png" width="350" title="inspector"></p>
- provides options for editing audio clips (`Volume`, `Pan`, `Pitch`, and `EQ`)
- to copy and paste `Inspector` attributes from one clip to another use shortcuts
- can add visual FX to clips: choose an effect from the `Effects Library` (top left corner) and drag it to a particular clip in a timeline; adjust the settings in the `Inspector`
    <p style="text-align:center;"><img src="data/edit - openfx.png" width="350" title="visual effects"></p>


### 4.5. Keyframing

Frequently in the edit, you want to *keyframe* adjustments that you're making in the `Inspector` (start one way and finish another).

- one example of this is manual version of the *dynamic zoom*, to create the same effect, use `Transform` tool, but set *keyframes* at particular moments of a clip (in the `Inspector`)
    <p style="text-align:center;"><img src="data/edit - keyframes.png" width="350" title="keyframes"></p>
- can adjust *keyframe* points with *keyframe tool* and *keyframe editor* (icons at the bottom right corner of a clip in a timeline)
    <p style="text-align:center;"><img src="data/edit - keyframe editor.png" width="350" title="keyframe editor"></p>


### 4.6. Speed ramping

*Resolve* allows to speed ramp the clips in the project (speed them up or slow them down).

- RMB on a clip and `Retime Controls` to make adjustments: add *speed points*, change speed, freeze frames, etc.
- RMB on a clip and `Retime Curve` for even more controls
- to delete all the *speed points* from a clip go back to the `Retime Controls`, click on a clip, and choose `Reset Clip` option
    <p style="text-align:center;"><img src="data/edit - retime controls.png" width="500" title="retime controls"></p>


-------------------------------------------------------------------------------
## 5. Color Page

### 5.1. Overview

#### Gallery

- `Gallery` is a place for stills (used as color correction presets and to compare shots to each other)
    <p style="text-align:center;"><img src="data/color - gallery.png" width="500" title="gallery"></p>
- can have bins of galleries and stills (e.g. *power grades* are bins for stills accessable from every project in a database)
- RMB in the viewer and `Grab Still` to save a still from the shot
- to compare selected shot with a still from the library RMB in the viewer and `Show Reference Wipe` (additional controls at the top right corner, dissable button at the top left corner)
    <p style="text-align:center;"><img src="data/color - still.png" width="500" title="still"></p>

#### UI and viewer

- to give more screen space for a viewer you can hide `Timeline` and `Clips` panels; also use UI presets (see [1.4.](#14-global-preferences))
- predefined *viewer modes* (`Workspace` → `Viewer Mode`): *Cinema Viewer*, *Enhanced Viewer*, and *Full Page Viewer* (can use shortcuts)
- can bypass all color corrections (button at the top right corner)

#### OpenFX

- place for visual effects (can use search)
    <p style="text-align:center;"><img src="data/color - openfx.png" width="350" title="openfx"></p>

#### Lightbox

- shows entire timeline in timeline order (one shot after another)
- can color grade the shots from this panel (top right corner to show color grading tools)
    <p style="text-align:center;"><img src="data/color - lightbox.png" width="500" title="lightbox"></p>

#### Waveforms

- can put them in a separate floating window (button at the top right corner, or use a shortcut)
- can change which waveforms show up (*RGB parade*, *waveform*, *vectorscope*, *histogram*, and *CIE chromaticity*)
- can adjust *waveforms* options (top right corner), e.g. show only lows, mids or highs in the *vectorscope*
    <p style="text-align:center;"><img src="data/color - waveforms.png" width="750" title="waveforms"></p>

#### Info palette and keyframes

- keyframe panel provides control over keyframes
    <p style="text-align:center;"><img src="data/color - keyframes.png" width="400" title="keyframes"></p>
- info palette shows metadata for selected shot
    <p style="text-align:center;"><img src="data/color - info.png" width="400" title="info"></p>


### 5.2. Color wheels (overview)

- four primary wheels: **lift** (shadows), **gamma** (midtones), **gain** (highlights), **offset**
- three implementations (top right corner):
    - **primary wheels**
        <p style="text-align:center;"><img src="data/color - primary wheels.png" width="550" title="color wheels"></p>
    - **primary bars** (allow to adjust a particular color channel, but *Resolve* will make counteractions to leave the overall brightness the same)
        <p style="text-align:center;"><img src="data/color - primary bars.png" width="550" title="color bars"></p>
    - **log** (logarithmic?)
- if a shot has *fade ups* or *dissolves*, turn `Unmix` button on (bottom left corner of the viewer) to ignore their effects on color corrections
- can make instant color adjustments (<kbd>Shift</kbd> + LMB on a color wheel)
- undo corrections:
    - `Color` → `Reset` → `All Grades and Nodes` to reset all color corrections
    - only color: double click on a wheel
    - color and exposure: *reset* button (top right corners of the color wheels)
- don't confuse color bias with the presence of objects of a particular color in the shot (e.g. a red shirt will be seen in the vectorscope)


### 5.3. Color wheels (workflow)

0. **Color Offset** (to remove overall *color cast* if needed)
1. **Contrast adjustments** (first because it has more effect on colors than otherwise)
    - by adjusting the contrast of *gamma* and *lift* wheels make sure nothing is clipped off
    - looking at the viewer, adjust the overall brightness of the shot using the contrast slide of the *gain* wheel
2. **Color adjustments**
    - looking at the *RGB parade*, balance the colors (if needed)
    - adjust *lift* and *gain* first, then *gamma* (because of overlaps between the wheels)
    - also use the *vectorscope* in the mids mode for monitoring if there is a color bias (white blob should be centered)
    - can additionally adjust *temp* (moves between blue and red) and *tint* (moves between magenta and green) from the `2` below the color wheels
3. **Saturation** (from the `1` below the color wheels)


### 5.4. Waveforms

The more you look at an image, the more correct it looks (same with audio). To fight this effect while adjusting colors we use `Waveforms` panel that gives an objective look of what's happening.

To understand better what *color wheels* do lets use them on a *greyscale*:

1. **Creating a greyscale**
    - go to the *Edit Page* and create a new timeline (`File` → `New Timeline...`)
    - `Effects Library` → *Generators* → *Grey Scale* and drop it to the timeline
    - RMB on the generator in the timeline and `New Compound Clip...`
        <p style="text-align:center;"><img src="data/color - greyscale init.png" width="550" title="greyscale init"></p>

2. **Contrast**
    - adjusting the exposure slide of the *gain wheel*
        <p style="text-align:center;"><img src="data/color - greyscale gain.png" width="550" title="greyscale gain"></p>
    - adjusting the exposure slide of the *lift wheel*
        <p style="text-align:center;"><img src="data/color - greyscale lift.png" width="550" title="greyscale lift"></p>
    - adjusting the exposure slide of the *gamma wheel*
        <p style="text-align:center;"><img src="data/color - greyscale gamma.png" width="550" title="greyscale gamma"></p>

3. **Color**
    - adjusting the *gain* color wheel
        <p style="text-align:center;"><img src="data/color - greyscale gain color.png" width="550" title="greyscale gain"></p>
    - adjusting the *lift* color wheel
        <p style="text-align:center;"><img src="data/color - greyscale lift color.png" width="550" title="greyscale lift"></p>
    - adjusting the *gamma* color wheel
        <p style="text-align:center;"><img src="data/color - greyscale gamma color.png" width="550" title="greyscale gamma"></p>


### 5.5. Automatic color correction

*Resolve* auto color correction tools have a tendency to overcorrect (push highlights too high, and shadows too low), but it does that to get the mid tones right.

1. Auto correction (`Auto Balance` below the `Color Wheels` panel)
    <p style="text-align:center;"><img src="data/color - auto balance.png" width="250" title="auto balance"></p>
2. Adjust the contrast slide of the *lift* and *gain* wheels to bring back the details and avoid clipping
3. Dial back the *saturation* (if needed)


### 5.6. Copy correction settings

Can also copy color correction settings from one shot to another.

- method 1:
    1. Select a shot you want to color correct
    2. MMB on the shot you want to copy the settings from
- method 2:
    1. Select a shot you want to color correct
    2. RMB on the shot you want to match (not exactly) the settings from and `Shot Match to this Clip`

<p style="text-align:center;"><img src="data/color - copy settings.png" width="250" title="copy settings"></p>


### 5.7. Node-based color correction

One of the defining characteristics of color correcting in *Resolve* is working in the `Node Tree`. Do one correction per node (this way you can easily disable a particular adjustment) and create node chains.

<p style="text-align:center;"><img src="data/color - node tree.png" width="400" title="node tree"></p>

- can *drag* the nodes around, *extract* them (see shortcuts), and *place* them between other nodes
- add a new node: RMB and `Add Node` → `Add Serial` (also see shortcuts)
- delete a node by selecting it and pressing <kbd>Delete</kbd>
- copy and paste node settings (see shortcuts)
- bypass a node by clicking on its number (bottom left corner)
- reset a node corrections with RMB and `Reset Node Grade`
- `Color` → `Reset`:
    - `Selected Node Grade`: reset the corrections in a selected node
    - `Grades but Keep Nodes`: reset the entire node tree, but keep structure
    - `All Grades and Nodes`: reset the entire node tree


### 5.8. Gallery

One of the key skills in color correction is shot matching, because more often than not you are color correcting multiple images at the same time, which have to to look like it's one continuous story. `Gallery` helps with that.

- organize stills with albums (bins on the left side of the `Gallery`)
- expanded `Gallery` view (button at the right corner):
    <p style="text-align:center;"><img src="data/color - expanded gallery.png" width="700" title="expanded gallery"></p>
    - can search through prebuilt color effects
    - can modify prebuilt effects in the `Nodes` panel
    - drop a still to the project by draging it from the `Group Stills` (top right) to the `Project Stills` (bottom right)
- by default, when you hover over a still in the `Gallery` it will be applied to the current shot in the viewer (to disable `...` in the right corner and toggle off `Live Preview`)
    <p style="text-align:center;"><img src="data/color - apply still.png" width="600" title="apply still"></p>
- grab a still to the `Gallery` from the shot: RMB in the viewer and `Grab Still`
- apply a still to a shot: select a shot (in the `Clips` panel) and MMB on a reference still (in the `Gallery`)
- name a still: RMB on a still and `Change Label`
- show a node tree of a still: RMB on a still and `Display Node Graph`
    <p style="text-align:center;"><img src="data/color - node graph.png" width="600" title="node graph"></p>


### 5.9. Curves

*Curves* can be used both for broad and for targeted color corrections. *Resolve* provides multiple *curves* tools, main one is the *custom curves*. And like when using *color wheels*, monitor your adjustments in the `Waveforms` panel.

<p style="text-align:center;"><img src="data/color - curves.png" width="500" title="curves"></p>

- can put *control points* on a curve to use them for targeted adjustments (click on a curve)
- can use *curves* for contrast adjustments (just like *color wheels*):
    - put a point above the brightest pixel and adjust the highlights
    - put a point below the dimmest pixel and adjust the shadows
    - put a point in the middle and adjust the overall brightness
    <p style="text-align:center;"><img src="data/color - curves contrast I.png" width="500" title="curves contrast I"></p>
    <p style="text-align:center;"><img src="data/color - curves contrast II.png" width="500" title="curves contrast II"></p>
- can adjust individual color channels
- can make targeted color adjustment:
    - select a color channel
    - choose `Qualifier` tool (bottom left corner of the viewer)
    - click on the part of a shot you want to adjust (e.g. skin of a character), this will add a control point to the curve
    - adjust the curve


### 5.10. Versus curves

There is a couple of *versus curves* in *Resolve*: *Hue vs Hue*, *Hue vs Sat*, *Hue vs Lum*, *Lum vs Sat*, and *Sat vs Sat*.

#### Hue vs Hue

Useful if you want to target a specifically colored part of a shot and spin its hue around (e.g. change the color of a shirt).

- select a part of the shot with `Qualifier` tool, this will add control points to the curve
    <p style="text-align:center;"><img src="data/color - hue vs hue I.png" width="600" title="hue vs hue I"></p>
- rotate the hue (can also adjust control points to make sure other objects in the shot are not modified)
    <p style="text-align:center;"><img src="data/color - hue vs hue II.png" width="600" title="hue vs hue II"></p>

#### Hue vs Sat

Useful if you want to target saturation level of specifically colored parts of a shot (e.g. saturate a red shirt).

- select `Qualifier` tool and click on a part of a shot you want to target, this will add control points to the curve
    <p style="text-align:center;"><img src="data/color - hue vs sat I.png" width="600" title="hue vs sat I"></p>
- adjust saturation (can also adjust control points to make sure other objects in the shot are not modified)
    <p style="text-align:center;"><img src="data/color - hue vs sat II.png" width="600" title="hue vs sat II"></p>

#### Sat vs Sat

Useful if you want to adjust a saturation of parts of a shot with a particular saturation value (e.g. change the saturation in the shadows).

- add a control point (e.g. in shadows)
    <p style="text-align:center;"><img src="data/color - sat vs sat I.png" width="500" title="sat vs sat I"></p>
- adjust the saturation
    <p style="text-align:center;"><img src="data/color - sat vs sat II.png" width="500" title="sat vs sat II"></p>


### 5.11. HSL keyer

**HLS keyer** (hue, luminance, saturation) is the most basic tool for targeted color corrections (was available before the were *curves* tools).

<p style="text-align:center;"><img src="data/color - HSL keyer.png" width="500" title="HSL keyer"></p>

- can select a color and rotate the hue
- useful for isolating brightness values in order to adjust the image, e.g. for isolating the highlights:
    - toggle on the *highlights mode* in the viewer (top left corner)
    - select a *luminance* range
    - control `L. Soft` and `Blur Radius` to soften the selection
    - now you can modify only the highlights of the shot
    <p style="text-align:center;"><img src="data/color - HSL highlights.png" width="600" title="HSL highlights"></p>


### 5.12. Power windows

Used to physically isolate parts of the shot (to modify only them).

<p style="text-align:center;"><img src="data/color - power window.png" width="500" title="power window"></p>

- several pre-built selection shapes: *linear*, *circle*, *polygon*, *curve*, and *gradient*
- select *Power Window* (bottom left corner of the viewer) to see on-screen selection widgets (but can also use the *highlights mode*)
- can adjust the shape, softness controls, and invert the selection
- usual workflow:
    - isolate the object using one of the available selection tools
        <p style="text-align:center;"><img src="data/color - power window selection I.png" width="350" title="power window selection I"></p>
    - invert the selection (if needed, e.g. for background)
        <p style="text-align:center;"><img src="data/color - power window selection II.png" width="350" title="power window selection II"></p>
    - modify the selection (e.g. dim the contrast of the background)
        <p style="text-align:center;"><img src="data/color - power window selection III.png" width="700" title="power window selection III"></p>
- can track selected objects with the `Tracker` tool:
    - isolate the object using `Power Window` tool
    - select the `Tracker` tool and choose appropriate options for the shot (enable or disable *pan*, *tilt*, *zoom*, *rotate*, and *3D* automatic tracking)
    - `Track Forward` and `Track Reverse` (top left corner) to track the object
        <p style="text-align:center;"><img src="data/color - tracker.png" width="500" title="tracker"></p>


### 5.13. OpenFX

- can apply OpenFX effects to nodes (drag an effect from the `OpenFX` panel)
- can modify effect settings
    <p style="text-align:center;"><img src="data/color - openfx settings.png" width="300" title="openfx settings"></p>
- sometimes you can use the *Colorize* tool
- to remove the effect from a node RMB and `Remove OFX plugin`


-------------------------------------------------------------------------------
## 6. Visual effects and audio mixing

### 6.1. Fusion title generator

- the most basic *fusion effects* are *titles*: *Edit Page* → `Effects Library` → *Titles* → *Fusion Titles* (marked with a lighting bolt symbol)
    <p style="text-align:center;"><img src="data/fusion - effects library.png" width="300" title="effects library"></p>
- add title effects to the timeline by dragging them there
    <p style="text-align:center;"><img src="data/fusion - title.png" width="200" title="title"></p>
- change various *Fusion* settings in the `Inspector`
    <p style="text-align:center;"><img src="data/fusion - title inspector.png" width="300" title="title inspector"></p>
- if an effect doesn't render properly in the timeline: `Project Settings` → `Master Settings` → set `Optimized Media Format` and `Render Cache Format` to `DNxHR HQ`; also can speed up the rendering by setting `Enable background caching` to 1 second
- to save an adjusted custom effect for later use just drag it to the `Media Pool` (can create a separate bin for this)


### 6.2. Fusion page

*Fusion* is a full-featured visual effects compositing package.

- RMB and `Ungroup` on a *fusion comp (composition)* to show a chain of nodes it consists of
    <p style="text-align:center;"><img src="data/fusion - effect.png" width="750" title="fusion effect"></p>
- adjust the settings of a node in the `Inspector`
- adjust the settings for the *Fusion Page*: `Fusion` → `Fusion settings...`
- there is a big list of *fusion tools* (<kbd>Ctrl</kbd> + <kbd>Space</kbd>)
    <p style="text-align:center;"><img src="data/fusion - tools.png" width="200" title="fusion tools"></p>


### 6.3. Fairlight page

*Fairlight Page* gives you the basic DAW functionality, and it's completely integrated into *DaVinci Resolve*.

<p style="text-align:center;"><img src="data/fairlight - timeline.png" width="550" title="fairlight timeline"></p>

- control clips settings in the `Inspector` (volume, pan, pitch, and EQ), and tracks settings in the `Mixer`
- can change the *timeline view options* and add *scrollers* (two audio scrollers to assign them to audio tracks, and one video scroller)
    <p style="text-align:center;"><img src="data/fairlight - scrollers.png" width="450" title="fairlight scrollers"></p>
- additional features:
    - create test tones with `Fairlight` → `Test Tones Settings...`
        <p style="text-align:center;"><img src="data/fairlight - test tones.png" width="350" title="fairlight test tones"></p>
    - with a dual screen set up, you can pop out the viewer to the second monitor (button at the bottom right corner of the viewer)
    - immersive controls (i.e. mixing in 3D space): `Fairlight` → `Immersive` → `Spaceview scope...` (only in *Resolve Studio*)


### 6.4. Audio editing and mixing

- can use *range selection mode*
    <p style="text-align:center;"><img src="data/fairlight - range selection.png" width="250" title="fairlight range selection"></p>
- there are several ways of adding *cross-fades* between clips:
    1. zoom in, RMB on the edit and `Add Cross Fade`
        <p style="text-align:center;"><img src="data/fairlight - simple crossfade.png" width="200" title="fairlight crossfade"></p>
    2. create *fade in* and *fade out* on the edges of the clips, enable `Timeline` → `Layered Audio Editing`, and drag one edge over another
        <p style="text-align:center;"><img src="data/fairlight - layered crossfade.png" width="200" title="fairlight crossfade"></p>
- *Fairlight* provides usual audio mixing tools:
    - *channel strips* in the `Mixer` (add effects, inserts, EQ, panning, etc.)
    - can add *busses* with `Fairlight` → `Buss Format...`
    - `Fairlight` → `Buss Assign...` to control *routing*
- *loudness meters* at the top right
    <p style="text-align:center;"><img src="data/fairlight - loudness.png" width="300" title="fairlight loudness"></p>


-------------------------------------------------------------------------------
## 7. Rendering and delivery

### 7.1 Deliver page

- *Resolve* gives a list of rendering presets to choose from (YouTube, Vimeo, H.264, etc.), or you can use your own settings (custom)
    <p style="text-align:center;"><img src="data/deliver - render settings.png" width="300" title="render settings"></p>
- first you add jobs to the `Render Queue` and only then render
    <p style="text-align:center;"><img src="data/deliver - render queue.png" width="300" title="render queue"></p>
- can save your presets (`...` and `Save As New Preset`)


### 7.2. Additional resources

- `Help` → `DaVinci Resolve Reference Manual` and `DaVinci Resolve Training`
- https://forum.blackmagicdesign.com/ (*Resolve* forum)
- www.liftgammagain.com/forum (color-correction centered)
- www.mixinglight.com
- books recommendations:
    - *Color Correction Handbook* by Alexis Van Hurkman
    - *The Art and Technique of Digital Color Correction* by Steve Hullfish

