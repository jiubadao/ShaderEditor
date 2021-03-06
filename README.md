Shader Editor
=============

Create and edit [GLSL](https://en.wikipedia.org/wiki/GLSL) shaders on
your Android phone or tablet and use them as live wallpaper.

<a href="https://play.google.com/store/apps/details?id=de.markusfisch.android.shadereditor&utm_source=global_co&utm_medium=prtnr&utm_content=Mar2515&utm_campaign=PartBadge&pcampaignid=MKT-AC-global-none-all-co-pr-py-PartBadges-Oct1515-1"><img alt="Get it on Google Play" src="https://play.google.com/intl/en_us/badges/images/apps/en-play-badge.png" height="45px"/></a>

[![Shader Editor on fdroid.org](https://f-droid.org/wiki/images/c/ca/F-Droid-button_available-on_smaller.png)](https://f-droid.org/repository/browse/?fdfilter=Shader+Editor&fdid=de.markusfisch.android.shadereditor)

Features
--------

* Live preview in background or on an extra screen
* Syntax highlighting
* Error highlighting
* Use any shader as live wallpaper
* Exposure of sensors (camera, accelerometer, gyroscope, magnetic field,
	light, pressure, proximity)
* Exposure of battery level
* Supports wallpaper offset
* Supports multiple touches
* Supports multiple render resolutions
* Previous rendered frame in backbuffer texture
* Import and use arbitrary textures
* Create and use cube maps
* Disables rendering when battery is low

FAQ
---

### How many FPS should I get to set my shader as live wallpaper?

Some devices limit GPU usage to consume less power when not plugged in.
Always check the performance with the soft keyboard hidden and the power
cord off. A shader should make at least around 30 fps to not slow down
the UI.

### How much battery will a live wallpaper take?

A live wallpaper should only consume battery when you see it.
So it generally depends on how often and how long you look at it.
With normal use, you shouldn't note a difference in battery consumption.

### What if errors are not highlighted?

Unfortunately error information is disabled on some devices (e.g. Huawei
Ideos X3, Asus Transformer). Error highlighting/reporting is not possible
on these devices.

### `time` uniform loses accuracy / framerate drops over time

Most probably it's because `time` is just a float of medium precision
(unfortunately the default for fragment shaders).
Either try to specify high precision (what may not be available on your
hardware):

```glsl
#ifdef GL_FRAGMENT_PRECISION_HIGH
precision highp float;
#else
precision mediump float;
#endif
```

Or use the `second`/`subsecond`/`ftime` uniforms instead.
See issue [#10](https://github.com/markusfisch/ShaderEditor/issues/10#issuecomment-160463706) for details.

### Where can I learn more about Shaders?

#### Basics

* [The Book of Shaders](http://thebookofshaders.com/)
* [An Introduction to Shaders](https://aerotwist.com/tutorials/an-introduction-to-shaders-part-1/)

#### Advanced

* [The OpenGL® ES Shading Language](https://www.khronos.org/files/opengles_shading_language.pdf)
* [OpenGL API documentation](http://docs.gl/)
* [GLSL Programming](https://en.wikibooks.org/wiki/GLSL_Programming)
* [Best Practices for Shaders](https://developer.apple.com/library/content/documentation/3DDrawing/Conceptual/OpenGLES_ProgrammingGuide/BestPracticesforShaders/BestPracticesforShaders.html)
