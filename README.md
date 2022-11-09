<br/>
<p align="center">
    <img src="https://raw.githubusercontent.com/Jaysmito101/cgl/main/logo.png" border="0"></
</p>

<br/>
<p align="center">
  <img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/Jaysmito101/cgl?style=for-the-badge">
  <img alt="Lines of code" src="https://img.shields.io/tokei/lines/github/Jaysmito101/cgl?style=for-the-badge">
  <img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/w/Jaysmito101/cgl?style=for-the-badge">
    <br>
    <img alt="Maintenance" src="https://img.shields.io/maintenance/yes/2022?style=for-the-badge">
    <a href="https://patreon.com/jaysmito101"><img src="https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Djaysmito101%26type%3Dpledges&style=for-the-badge" alt="Support me on Patreon" /></a>
</p>
<br/>


# CGL
CGL (C Graphics Library) is a multipurpose library mainly for recreational coding /  demo scenes / prototyping / small games / experimentation. This has a lot of utilities for graphics. And best of all all of it is inside a single header file `cgl.h`.  Also CGL is made purely in C but is also compatible with C++. 

NOTE: Do not think that header only means its going to increase compile time as the implementation needs be enabled only for 1 file using `#define CGL_IMPLEMENTATION`

[Examples](./examples)

## Target Platforms
* Windows
* Linux
* MacOS (untested)
* WebAssembly (Beta)
* Android (Comming soon...)

## What does CGL provide?

* Windowing library (Optional)
  - You can completely disable it by `#define CGL_EXCLUDE_WINDOW_API`
  - This windowing library is primarily a wrapper GLFW along with a few extra functionalities. For example in case you are using some library like `nuklear` for GUI it will mess up all `glfw` callbacks so with CGL you can restore the CGL callbacks with a call to `CGL_window_resecure_callbacks`

* Utility functionalities
  - Reading/Writing files
  - Random float/int/bool/vec2/vec3/color generation
  - CRC32/CRC64
  - ROT13 encryption
  - General Purpose Hashing Functions [refer here]( http://www.azillionmonkeys.com/qed/hash.html)
  - Colored printf (red, green, blue, gray/yellow)
  - TODO: [ MD5 / SHA 256 / SHA 128 / AES ]

* Data structures
  - List(dynamic array) + Stack (implemented together)
  - Hashtable -> This hastable is general purpose. Key can be string or a n-bit buffer. The value can be anything int, string, float, custom types, ...
     - Hashtable Iterator -> Iterate through the hashtable using a [simple](https://github.com/Jaysmito101/cgl/blob/main/examples/using_hashtable_iterator.c) API
  
* Logger
  - Can be enabled/disabled by `#define CGL_DISABLE_LOGGER`
  - Log to multiple log files simultaneously
  - Log to console with colored output for seperate log levels
  - Logger with auto timestamps
  
* Cross Platform Networking (Optional)
  - You can disable all networking by `#define CGL_EXCLUDE_NETWORKING`
  - Low-level sockets 
  - SSL sockets (optional) (requires  OpenSSL)
  - HTTP/HTTPS request (beta)
  
* General Purpose Markov Chains (Optional) [Example](./examples/markov_text_generation.c)
  - Can work with any type of data ( text / image / etc.  )
  - Train/Generate with 3 - 4 lines of code
  - Trainer implemented for text generation (n-gram based)
  - Custom trainer API for custom scenarios
  
* Cross Platform Threading
  - Threads
  - Mutex
  - Condition Variables (TODO)
  - NOTE: Implemented using `Win32 Threads` on Windows and `pthread` on Linux. (on Linux you need to link `pthread` to build)

* CGL Widgets (Optional)
  - You can disable it by `#define CGL_EXCLUDE_WIDGETS`
  - API Like [p5.js](https://p5js.org/)
  - Batch Renderer backend (very fast even for a large number of widgets)
  - draw (filled or stroked) :
    - triangle [`CGL_widgets_add_triangle`]
    - general quad [`CGL_widgets_add_quad`]
    - rectangle [`CGL_widgets_add_rect` `CGL_widgets_add_rect2f`]
    - line [`CGL_widgets_add_line`]
    - circle [`CGL_widgets_add_circle` `CGL_widgets_add_circle2f`]
    - oval [`CGL_widgets_add_oval`, `CGL_widgets_add_oval2f`]
  - Add individual vertices
  - Adjust stroke color/thickness
  - Customize Batch renderer max vertices capacity (for low memory systems)

* Math library
  - vec2/vec3/vec4
  - mat3/mat4
  - add/sub/mul/div/scale/length/normalize/lerp/min/max/equal for vec2/vec3/vec4
  - rotate_x/rotate_y/rotate_z for vec3
  - scale/translate/rotate_x/rotate_y/rotate_z/add/sub/mul for mat4
  - perspective for mat4
  - transpose for mat4/(mat3 TODO)
  - look_at matrix 
  - NOTE: Most of math functions are implemented via macros so will be totally inclined and quite fast without any unnecessary function calls

* High Level OpenGL API for (Optional)
  - You can completely disable it by `#define CGL_EXCLUDE_GRAPHICS_API`
  - Texture (2D / 2D Array / Cube map) 
  - Framebuffers
  - SSBO (Shader Storage Buffer Object)
  - Shaders 
    - Vertex & Fragment (Geometry Shader not included as its not very widely used)
    - Compute Shader API 

* CGL Mesh API
  - CGL has a high level API for handling meshes
  - 2 types of meshes are there
    - CPU mesh -> stores the data also used for mesh operations like
      - generate triangle
      - generate quad
      - load OBJ (beta)
      - generate cube
      - generate sphere
      - generate mesh out of any parametric surface function [refer here](https://stackoverflow.com/a/31326534/14911094)
      - calculate normals (TODO)
    - GPU mesh -> the pointer to the data stored on GPU side (internally handles the Vertex buffer, Index buffer, Vertex Array) and can used for
      - render
      - render instanced
      - render wireframe
      - render wireframe instanced
      
* CGL camera
  - CGL provides a proper camera abstraction
  - Perspective & Orthographic
  - It internally handles all matrix calculations (just input the position and rotation)
  - Auto calculates the Up, Right, Front vectors
 
* Text Rendering (Optional) (Requires [FreeType2](http://freetype.org/))
  - You can completely disable it with `#define CGL_EXCLUDE_TEXT_RENDER`
  - Load Fonts from `.ttf` files
  - Bake bitmaps for characters
  - Bake textures from strings
  
 
* Sky Renderer (Optional)
  - You can completely disable it with `#define CGL_EXCLUDE_SKY_RENDERER`
  - Supports both a Sky Box (cube mesh) and Sky Sphere/Dome (sphere mesh)
  - Supports Cube map Textured Sky 
  - Supports Realtime Procedurally Generated Sky ( + procedural clouds)
  - Render a beautiful sky with just 3 - 5 lines of code

* Phong Renderer (Optional) 
  - You can disable it via `#define CGL_EXCLUDE_PHONG_RENDERER`
  - It has:
    - Phone Pipeline -> it is the pipeline holding shader data and global engine data. Options available are
      - enable/disable blinn correction
      - enable/disable depth test
      - enable/disable gamma correction
      - setup ambient lighting
      - add/remove lights
    - Phong Light -> It can be of 3 types:
      - Directional -> it takes (direction, color, intensity)
      - Point -> it takes (position, color, itensity, constant, linear, quadratic)
      - Spot (TODO)
    - Phong Material
      - dissuse texture/color
      - specular texture/color
      - shininess
      - normal maps (TODO)

* Tilemap Renderer (Optional)
   - You can disable it with `#define CGL_EXCLUDE_TILEMAP_RENDERER`
   - Renders a NxN tilemap with a single line of code
   - Each tile can have following states
     - clear (transparent or disabled)
     - solid color
     - texture -> Texture can be supplied via:
       - texture 2d array -> you need to provide depth for each tile
       - tileset or texture atlas -> you have to provide bounds (normalized 0.0-1.0) of the area of the alas to be used on tile
    - NOTE: this tile render renders only 4 vertices and has only 1 draw call  (not a instanced call so its quite fast
    
 ## Things that are being worked on:
 
 * PBR renderer (optional)
 * IBL (optional)
 
## Requirements 

* GLFW
* Glad
