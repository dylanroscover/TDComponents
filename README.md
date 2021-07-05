# TDComponents

A collection of small components that make every day life in TouchDesigner slightly more bearable.

---


## :artist: colorCurves

colorCurves graphically adjusts per-channel color levels of a TOP using a plotted curve, similar to many image and video editing applications. Credit goes to [Vasily](https://derivative.ca/community-post/asset/color-curves) for authoring the original version of this component, to which I built onto.

![colorCurves Screenshot](/img/colorCurvesScreenshot.png)

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

## :old_key: Keyframer

Keyframer plays animations similar to an Animation COMP setup, but with more advanced cueing, playback and COMP integration features.

### Pars

#### General

* `Target COMP` - The desired COMP you wish to animate. A Geometry COMP with a `constant1` material inside is recommended. Once specified, target channels named `t[xyz]`, `r[xyz]`, `s[xyz` or `opacity` will automatically be connected via expressions.

* `Target Channel Name (1-4)` - The name of each target channels. These can be any name, however channels named `t[xyz]`, `r[xyz]`, `s[xyz` or `opacity` will automatically be connected via expressions once the `Target COMP` parameter is specified. Note that only up to 4 channels can be used in each Keyframer instance. If more are required, create new Keyframer instances.

#### Playback

* `Start to End Blend` - Defines the curve interpolation between the intro transition and outro transition (the 'hold' section of the animation).

* `Perform Mode` - Toggles between Python-driven playback and CHOP-driven playback. While CHOP-driven playback is slightly more efficient, it is prone to more bugs. Python (`Perform Mode` set to `False`) is recommended for more complex configurations.

* `Current Frame Index` - Sets the current frame of the animation. Useful as a scrubbing tool to trace the movement of animations while editing. Automatically updates during playback.

* `Play Anim` - Plays/resets the animation. Resetting (setting `Play Anim` to False) is the equivalent of cueing the animation back to it's first frame (0). Automatically resets at the completion of non-looping animations.

* `Pause Anim` - Pauses the animation. Setting to `False` resumes the animation if `Play Anim` is enabled.

* `Exit Anim` - Jumps the animation to the first frame of the outro transition and continues playback until the animation has fully exited (played out and reset to first frame). Useful for exiting an animation at a specific cue event.

* `Loop Anim` - Loops the animation (restarts indefnitely) when enabled. When disabled, the animation plays as a 'one-shot' (single playback) and then resets to the first frame (0).

* `Hold End Frame` - Holds on the end frame of the animation rather than resetting to the first frame (0). Useful if the end frame is a different value than the first frame, as this would otherwise cause a single jump frame at the very end of the exit.

#### Start

* `Cue Frame` - The first frame of the animation to play from. Useful if the animation must be entered from a different point than the `Start Frame` (the very beginning of the animation curve), such as instances where the intro transition must be skipped. The `Play Anim` parameter will always start playback from this value.

* `Start Frame` - The very beginning of the animation curve and where the intro transition begins. This can be set to a higher value than 0 if a delay in the intro transition is desired.

* `Start Length (Frames)` - The length of the intro transition (an s-curve that goes from a `Start In` value to a `Start Out` value).

* `Start In Value (1-4)` - Each channel's initial value during the intro transition.

* `Start Out Value (1-4)` - Each channel's end value during the intro transition.

* `Start Curve Type` - The intro transition's s-curve interpolation.

* `Start Steepness` - The steepness of the intro transition's s-curve.

* `Start Linearize` - How straight (linear) the intro transition's s-curve is.

* `Start Bias` - How quickly to the left (beginning) or right (end) the intro transition ramps up or down; that is, how dramatic it's curve ramps up or ramps down, depending on the bias.

#### End

* `End Frame` - The very end of the animation curve and where the outro transition ends.

* `End Length (Frames)` - The length of the outro transition (an s-curve that goes from an `End In` value to an `End Out` value).

* `End In Value (1-4)` - Each channel's initial value during the outro transition.

* `End Out Value (1-4)` - Each channel's end value during the outro transition.

* `End Curve Type` - The outro transition's s-curve interpolation.

* `End Steepness` - The steepness of the outro transition's s-curve.

* `End Linearize` - How straight (linear) the outro transition's s-curve is.

* `End Bias` - How quickly to the left (beginning) or right (end) the outro transition ramps up or down; that is, how dramatic it's curve ramps up or ramps down, depending on the bias.

---

## :man_cook: Lagger

Lagger dynamically disables cooking on Filter/Lag CHOPs while they are not changing values, saving you precious cook time.

### Pars

* `Input Value` - Sets the value to be smoothed via the Lag or Filter CHOP. A CHOP can also be wired via the component's In CHOP as the input.

* `Chan Name` - The name of the output CHOP channel. Useful if the channel needs to be renamed from the input.

* `Lag or Filter` - Switches between either the Lag CHOP or Filter CHOP as the method of channel handling.

* `Lag (s)` - The lag in/out times, in seconds, as corresponds to the Lag CHOP.

* `Filter Width` - The filter width, in seconds, as corresponds to the Filter CHOP.

* `Filter Type` - The type of filter to be used; default is Gaussian.


---

## :play_or_pause_button: Playback

Playback plays, scrubs, loops and fades movies in/out in a simple geometryCOMP setup.

### Pars

* `Active` - Fades the movie material alpha on/off.
* `Video File` - The video file that is played back.
* `One-shot or Loop` - Plays the video file once or loops it forever. Can be switched during playback for advanced workflows.
* `Play` - Plays/pauses the video playback.
* `Scrub` - Scrubs the video file from start to finish. 0.0 is the first frame of the file, 1.0 is the last frame. Can be scrubbed at anytime. Setting to 0.0 is the equivalent of cueing the video.
* `Progress` - The current frame of the video being displayed (normalized fraction, same as `Scrub`).
* `Size` - The width and height of the rectangleSOP in which the video is displayed. This can be pixel values, or fractional values, depending on your scene setup and scale.