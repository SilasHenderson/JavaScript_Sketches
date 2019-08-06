# visual-math

The goal of the website is to write a bunch of *Short, All-in-one HTML Files* showing how to do
scientific computation/visualization *without installing anything*.

## Notes

### Graphics (2d vs. 3d)
The 2d-graphics are orthographic projections of 3d graphics with THREE.js.

### Graphics (General)
For meshes, THREE BufferGeometries are a good mix of fast and practical.  http://www.visual-math.com/static.html shows that a scene with 20,000 triangles (30,000 float buffer for color, 20,000 float buffer for vertices) can be set to specified values at at 60 fps.

### Selecting Elements / Mouse Support (2d axis)
If a single buffer-geometry is used for everything, then finding a way to select individual elements is a challenge.

#### Text and Labeling (on the canvas)
Writing text *on the webGL canvas* may be tricky.  Right now, it looks like there's three options:
* Import a 3d-text geometry.
* Import a collection of 2d-bitmap characters and paste them to surfaces.
* Superimpose a 2d drawing canvas on the 3d THREE.js canvas (see mechanical3 'canvas' button)

### Text and Labeling (outside the canvas)
A div element with the same size as the canvas could be used to display full-page text.   When a button is pressed, the z-index of the div element is moved up front and the THREE canvas is set to be invisible (tested with mechanical3 'Div' button).

### Sushi
`Sushi` builds matrix objects from `Float32` typed arrays.  The library is a single 1000 line javascript file.  `Sushi` is fast for inverting matrices with size less-than 400x400.  Sushi has a version that runs calcs through webCL (30x faster), but webCL doesn't have default support in browsers.  
 
### Large Matrix Inversion with WASM and WebGL
Matrix inversion for matrices of size greater than [500, 500] in javascript may be problematic
Client-side accelerated math is possible but current implementations are still being developed.  Two critical tools are now available for making this happen:
* `Web Assembly` provides a sandbox for assembly language. An example implementation is AutoCad's new web app.
* `WebGL` provides access to the GPU.  Examples abound.

In the present, `Tensorflow.js` and `Sushi.js` are good choices for getting top-speed.

### Deep Learning's Relation to Open-Source Engineering Software:
Cutting-edge open-source math libraries are being developed for machine learning.  These libraries can also be used for engineering math.

### Resources 
Gilbert Strang's new course on linear algebra for deep learning.

https://youtu.be/Cx5Z-OslNWE

Dominic Kramer at Google talking about low-level tfjs api for linalg:

https://youtu.be/aHHZu-i5hpE

https://www.seas.upenn.edu/~cis565/Lectures2011/Lecture7.pdf

General Info on Shaders

https://processing.org/tutorials/pshader/

Image Processing on Shaders

https://www.objc.io/issues/21-camera-and-photos/gpu-accelerated-image-processing/

Web Assembly Studio

https://webassembly.studio/

C++ --> WASM

https://anonyco.github.io/WasmFiddlePlusPlus/

WA Documentation

https://developer.mozilla.org/en-US/docs/WebAssembly

https://webassembly.org/docs/semantics/

WebGL Compute Shaders Examples

https://github.com/9ballsyndrome/WebGL_Compute_shader

WebGL Compute Shader Spec

https://www.khronos.org/registry/webgl/specs/latest/2.0-compute/

Javascript Sparse Matrix Performance

https://dl.acm.org/citation.cfm?id=3237020

Sushi2

https://github.com/mil-tokyo/sushi2

Powerpoint on WebGL

https://www.khronos.org/assets/uploads/developers/library/2017-gdc-webgl-webvr-gltf-meetup/2%20-%20WebGL%202.0%20@%20Silicon%20Valley%20WebGL%20Meetup%20-%20Mar17.pdf

Update on Compute Shaders

https://groups.google.com/a/chromium.org/forum/#!msg/blink-dev/bPD47wqY-r8/5DzgvEwFBAAJ

Sushi-Lab

https://mil-tokyo.github.io/sushilab/?loadurl=notebooks/gettingstarted.json
