# 🎩 TDComponents

### A whimsical collection of components to sprinkle some joy into your TouchDesigner shenanigans.
#### 💾 TouchDesigner 2023.11760 (Windows)

- [chop_recorder.tox](#-chop-recorder) - [Download v0.2.8](https://github.com/dylanroscover/TDComponents/raw/main/release/chop_recorder-v0.2.8.tox)
- [color_curves.tox](#-color-curves) - [Download v2.3.4](https://github.com/dylanroscover/TDComponents/raw/main/release/color_curves-v2.3.4.tox)
- [comper.tox](#-comper) - [Download v2.0.6](https://github.com/dylanroscover/TDComponents/raw/main/release/comper-v2.0.6.tox)
- [hexler.tox](#hexler) - [Download v0.1.5](https://github.com/dylanroscover/TDComponents/raw/main/release/hexler-v0.1.5.tox)
- [optimeister.tox](#-optimeister) - [Download v0.6.53](https://github.com/dylanroscover/TDComponents/raw/main/release/optimeister-v0.6.53.tox)
- [masker.tox](#-masker) - [Download v0.4.4](https://github.com/dylanroscover/TDComponents/raw/main/release/masker-v0.4.4.tox)
- [playback.tox](#-playback) - [Download v0.2.38](https://github.com/dylanroscover/TDComponents/raw/main/release/playback-v0.2.38.tox)
- [step_n_repeat.tox](#-step-n-repeat) - [Download v1.0.2](https://github.com/dylanroscover/TDComponents/raw/main/release/step_n_repeat-v1.0.2.tox)
- [timecode.tox](#-timecode) - [Download v0.1.5](https://github.com/dylanroscover/TDComponents/raw/main/release/timecode-v0.1.5.tox)

---

## 🎬 Chop Recorder

Chop Recorder allows you to record multi-channel CHOPs in real time, to disk, and play them back later. It's perfect for LiDAR and MIDI data, providing a seamless way to capture and replay complex channel data within TouchDesigner.

### Features
- Real-time recording of multi-channel CHOPs
- Disk-based storage for efficient memory usage
- Playback functionality for recorded data
- Ideal for LiDAR, MIDI, and other multi-channel data sources

### Parameters

#### Recording
- `Active`: Enable/disable the recorder
- `Record`: Start/stop recording
- `Rec Progress`: Shows the recording progress
- `Length (sec)`: Set the recording duration
- `Rec Folder`: Specify the folder for saving recordings
- `Rec Filename`: Set the filename for the recording
- `Open Rec Folder`: Open the folder containing recordings

#### Playback
- `Active`: Enable/disable playback
- `File`: Select the file to play
- `Play`: Start/stop playback
- `Play Progress`: Shows the playback progress
- `One-shot or Loop`: Toggle between single playback or looping

### Usage
1. Connect your input CHOP to the `IN` input of the Chop Recorder.
2. Set the `Rec Folder` and `Rec Filename` parameters.
3. Set the desired `Length` for your recording.
4. Toggle `Record` to start recording. The `Rec Progress` will show the progress.
5. Once recorded, you can play back the file by setting the `File` parameter and toggling `Play`.
6. Use `One-shot or Loop` to control playback behavior.

---

## 🎨 Color Curves

ColorCurves graphically adjusts per-channel color levels of a TOP using a plotted curve, similar to many image and video editing applications. Credit goes to [Vasily](https://derivative.ca/community-post/asset/color-curves) for authoring the original version of this component, to which I built onto.

![Color Curves Screenshot](https://raw.githubusercontent.com/dylanroscover/TDComponents/main/img/colorCurvesScreenshot.png)

### Input
Any TOP can be fed into the component's input. Default is the TD Banana.

### Output
The component's output consists of the graded TOP.

### Usage

#### Channels
`Master` (all channels), `Red`, `Green` and `Blue` channels can be edited individually by selecting them from the top tab menu. All settings can be reset for all 4 channel editors by pulsing the `Reset All` button.

#### Adding/Editing Points
Click anywhere in the curve editor (the square with the thin white diagonal line crossing through it) to add a point at that location. Click and drag to move the point into your desired position. If you click and drag on an existing point, that point will be moved.

#### Removing Points
Right click on any point to remove it.

#### Interpolation
Default interpolation between points is `Linear`. You can select between `Step`, `Linear`, `Ease` and `Hermite` for various curve styles. If `Hermite` is selected, the `Hermite Tension` par slider allows you to further tune your curve.

#### Smoothing
In addition to interpolation, your curve can be smoothed out by increasing the `Smooth` par slider. By default it is set to `0.0` (no interpolation). This can be used in combination with any interpolation mode.

#### Preview / Levels
By default a Preview of your TOP is shown. If you toggle the `Preview` button, it will switch to a Levels display of your current channel, which shows the total amount of values (y axis) in your adjusted TOP, drawn from dark to bright values (x-axis).

#### Single / Split Views
By default a single view of the edited image is shown. To compare against the original, toggle the `Single View` button to the `Split View` mode, which draws a vertical bar in the curve editor that slides from left to right. The original TOP image is on the left, and the edited TOP is on the right.

#### Handles and Reset
The circle handles and curve line call additional draw functions via Render TOPs. To reduce compute in your project, these can be hidden via the `Handles` toggle button. 

Finally, the `Reset` button will reset the current channel being edited.

---

## 🤹 Comper

Comper is a texel-based composite GLSL component with position, rotation, scale, and alpha matte options for each layer. It allows for flexible and efficient compositing of multiple layers in TouchDesigner.

### Features
- Texel-based compositing using GLSL
- Per-layer control of position, rotation, and scale
- Alpha matte options for each layer
- Efficient GPU-based processing

### Parameters

#### General
- `Resolution`: Set the output resolution (width/height)
- `BG Colour`: Set the background color (RGBA)
- `Fractional Translate`: Enable/disable fractional translation
- `Pivot`: Set the pivot point for transformations

#### Layer Controls
- `TOP`: Select the input TOP for each layer
- `Level`: Adjust the opacity of each layer
- `Translate`: Set the X and Y translation for each layer
- `Rotate`: Set the rotation for each layer
- `Scale`: Set the X and Y scale for each layer
- `Matte Buffer`: Set the matte buffer color (RGBA) for each layer

### Usage
1. Set the desired output `Resolution`.
2. Add input TOPs to the `TOP` parameters for each layer you want to composite.
3. Adjust the `Level`, `Translate`, `Rotate`, and `Scale` parameters for each layer as needed.
4. Fine-tune the composition using the `Matte Buffer` and other advanced parameters.

---

## 🌈 Hexler

Hexler is a utility component that converts RGB color values to hexadecimal color codes and vice versa. This tool is perfect for designers and developers who need to work with different color formats in TouchDesigner.

### Features
- Convert RGB to Hex
- Convert Hex to RGB
- Easy-to-use interface

### Parameters
- `Hex`: Enter or display the hexadecimal color code
- `RGB`: Set or display the RGB color values (0-1 range)

### Usage
1. To convert from RGB to Hex:
   - Set the `RGB` values using the parameter sliders.
   - The corresponding `Hex` value will be automatically updated.

2. To convert from Hex to RGB:
   - Enter the hexadecimal color code in the `Hex` parameter.
   - The corresponding `RGB` values will be automatically updated.

---

## 👨‍🍳 Optimeister

Optimeister cooks common CHOP outputs only when their data changes. This considerably improves performance of complex networks with many downstream CHOPs following ones that typically always cook. Supported CHOPs include: Delay, Filter, Lag, Logic, Timer, Trigger, Speed, and Slope.

It accepts channel inputs via custom parameters or a single wire in, which can be multi-channel, allows for renaming of outputs, and the full customization of parameters bound to the CHOP operation specified (Delay/Filter/Lag/etc.).

### Parameters

#### General

* `Reinit` - Reinitializes the component, a sort of reset button.
* `Selectively Uncook Operation` - Bypass the main operation node (usually Filter or Lag CHOP) while it is not actively tweening data. Can greatly improve performance in environments with many instances of Optimeister. Note that this may not always function as intended, and should be disabled if any oddities with output data are observed.
* `Version` - Current version of the component, which can be compared with this repo to confirm the latest version.
* `Help` - Opens this webpage in a browser for the very section you're reading right now... help! #meta
* `GitHub` - Opens the main GitHub repo for downloading any updates to Optimeister.

#### Input

* `Use Wired Input` - Used to disable the use of the wired input instead of the Input parameters (Input0, Input1, etc.). Will automatically set itself when a wired input is connected, and vice-versa will disable itself when disconnected.
* `Num Inputs` - The total number of input channels. Can be set manually when Use Wired Input is disabled. Otherwise, it is set to Read Only and automatically updated to the number of input channels detected when wired input is used.
* `Input * Value` - Each input channel as a parameter. Can be referenced with `op('Optimeister').par.Input0`, etc. Set to Read Only when Use Wired Input is enabled to prevent data stream doubling. Supports expression and bind modes that reference external sources. Note that expression and bind modes will be disabled (reset to constant mode) when a wired input is detected.

#### Output

* `Use Input Channel Names` - When enabled all Output Channels will default to the input channel names if using wired inputs. If using custom parameters on the Input page, they will be Input0, Input1, Input2, etc. When disabled, the Output Channel Names parameters will become editable (instead of Read Only) and override the existing output values when changed. If this parameter is toggled, any edits made are retained in Python storage, so any custom channel names are not immediately lost.
* `Output Channel *` - The name of each output channel as a parameter, editable or Read Only depending on whether the Use Input Channel Names parameter is enabled or not.

#### Operation

* `Operation Type` - The type of CHOP that input data runs through; the intermediary of Optimeister. Supported Operators include: Delay, Filter, Lag, Logic, Timer, Trigger, Speed, and Slope. All parameters of the selected Operation Type are automatically added below this parameter and bound to the intermediary CHOP. This allows for easy external adjustments of settings without diving into the Optimeister base component (useful, for example, if Optimeister operates in a clone setup within a project.)

---

## 🎭 Masker

Masker is a powerful UI-based mask creation tool for TouchDesigner, allowing you to create and manipulate complex masks with an intuitive interface.

### Features
- Multiple mask layers with individual controls
- Real-time mask rendering and editing
- Customizable UI and output settings
- Support for curved and inverted masks
- Color and opacity controls for each mask

### Parameters

#### Masks
- **Active Mask**: Select the current mask to edit
- **Mask Name**: Name your masks for easy identification
- **Add/Remove Mask**: Create or delete mask layers
- **Mask Color**: Set the color of the current mask
- **Mask Opacity**: Adjust the transparency of the mask
- **Invert Mask**: Invert the selected mask
- **Curve Mask**: Enable curved edges for the mask
- **Delete Mask Points**: Remove all points from the current mask

#### UI
- **Render UI**: Toggle the visibility of the UI
- **UI Zoom/Pan**: Adjust the view of the mask editing area
- **Edit Point Size**: Change the size of control points
- **Show Artboard/Grid**: Display helpful visual guides

#### Output
- **Render Output**: Enable/disable mask rendering
- **Resolution**: Set the output resolution of the mask
- **Zoom**: Adjust the scale of the output

### Usage
1. Use the "Add Mask" button to create a new mask layer.
2. Select a mask from the "Active Mask" dropdown to edit it.
3. Click in the UI area to add points and shape your mask.
4. Adjust the mask's color, opacity, and other properties as needed.
5. Use the "Curve Mask" option for smooth, curved edges.
6. The final mask output can be accessed through the "Output Render Pass TOP".

This powerful and flexible masking tool allows for creative and precise mask creation directly within TouchDesigner, suitable for a wide range of visual effects and compositing tasks.

---

## ▶️ Playback

Playback plays, scrubs, loops and fades movies in/out in a simple geometryCOMP setup.

### Parameters

* `Active` - Fades the movie material alpha on/off.
* `Video File` - The video file that is played back.
* `One-shot or Loop` - Plays the video file once or loops it forever. Can be switched during playback for advanced workflows.
* `Crossfade (Sec)` - Sets the duration of the crossfade between loops or when switching videos.
* `Reload` - Reloads the current video file.
* `Play` - Plays/pauses the video playback.
* `Scrub` - Scrubs the video file from start to finish. 0.0 is the first frame of the file, 1.0 is the last frame. Can be scrubbed at anytime. Setting to 0.0 is the equivalent of cueing the video.
* `Progress` - The current frame of the video being displayed (normalized fraction, same as `Scrub`).
* `Size` - The width and height of the rectangleSOP in which the video is displayed. This can be pixel values, or fractional values, depending on your scene setup and scale.

### Usage
1. Set the `Video File` parameter to the path of your video file.
2. Adjust the `Size` parameter to fit your scene.
3. Toggle `Active` to fade the video in/out.
4. Use `Play` to start/pause playback, or `Scrub` to manually control the playback position.
5. Set `One-shot or Loop` based on your playback needs.
6. Adjust `Crossfade (Sec)` for smooth transitions between loops or video changes.

---

## 🧱 Step N Repeat

Step N Repeat is a GLSL-based component that creates a brick or grid pattern of a texture (like a logo) on top of a different background texture. It offers various sizing and layout options for flexible design possibilities.

### Features
- Create brick or grid patterns
- Customizable sizing and layout
- GLSL-based for efficient processing
- Combine foreground and background textures

### Parameters
- `Number of Tiles`: Set the number of tiles in X and Y directions
- `Tile Scale`: Adjust the scale of individual tiles
- `Pattern Mode`: Choose between "grid" and "brick" patterns
- `Premultiply Alpha`: Toggle alpha premultiplication

### Usage
1. Connect your logo texture to the `in_logo` input.
2. Connect your background texture to the `in_bg` input.
3. Adjust the `Number of Tiles` in X and Y to set the grid density.
4. Use `Tile Scale` to resize the individual tiles.
5. Select the desired `Pattern Mode` (grid or brick).
6. Toggle `Premultiply Alpha` based on your compositing needs.

The component will output a TOP with the repeated pattern of your logo over the background texture.

---

## ⏱️ Timecode

Timecode renders a TOP output of timecode (HH:MM:SS:FF) using 2D texture slicing instead of the Text TOP. This generally cooks about twice as fast as an equivalent Text TOP. It can be configured with a custom font, generate timecode from an internal timer setup, or receive a single row/column table DAT input.

![Timecode](https://raw.githubusercontent.com/dylanroscover/TDComponents/main/img/Timecode.gif)

### Parameters

#### Internal Timer

* `Use Timeline` - Use the timeline for timecode generation instead of the internal timer.
* `Use Internal Timer` - Enables/disables the internal Timer CHOP. Will auto-disable on a timer cycle if an external input is connected to the Timecode COMP input.
* `Init` - Initializes the internal Timer CHOP.
* `Start` - Starts the internal Timer CHOP.
* `Play` - Plays/pauses the internal Timer CHOP.
* `Cue` - Cues the internal Timer CHOP.
* `Length (s)` - Updates the length of the internal Timer CHOP, in