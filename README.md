# Bindless Deferred Texturing and Decals Sample

This project is a D3D12 rendering sample that implements a deferred renderer using bindless deferred texturing. Deferred texturing is similar to normal deferred rendering, except that textures are not sampled in the geometry pass. Instead, the interpolated UV's are written into the G-Buffer so that the material textures can be sampled during the deferred pass. To enable sampling of textures from arbitrary materials, the demo makes use of dynamic indexing of texture descriptors. The demo also implements a deferred decal system using a clustering technique that's compatible with both deferred texturing as well as clustered forward rendering (which is also implemented in the demo as a baseline for comparison).

See the full blog post for more info: [https://mynameismjp.wordpress.com/2016/03/25/bindless-texturing-for-deferred-rendering-and-decals/](https://mynameismjp.wordpress.com/2016/03/25/bindless-texturing-for-deferred-rendering-and-decals/)

# Build Instructions

The repository contains a Visual Studio 2015 project and solution file that's ready to build on Windows. All external dependencies are included in the repository, so there's no need to download additional libraries. Running the demo requires Windows 10, as well as a GPU that supports Feature Level 11_1.

# Using The Demo App

To move the camera, press the W/S/A/D/Q/E keys. The camera can also be rotated by right-clicking on the window and dragging the mouse. To place new decals, click the middle mouse button. Everything else is controlled through the in-app settings UI.

# Notes About The Experimental Branch

This branch features a new, experimental version of the sample framework that uses full bindless descriptor access for all SRV's. It also supports using the new [open-source HLSL compiler](https://github.com/Microsoft/DirectXShaderCompiler) with support for Shader Model 6.0. Usage of the new compiler is controlled by the "EnableShaderModel6_" macro that's defined in AppConfig.h. The compiler itself isn't included in this repo, so you'll need to build it yourself. Once you've built it, run SampleFramework12\v1.01\Scripts\CopyDXC.bat from the HLSL compiler command prompt to copy the necessary files into the "Externals" directory referenced by this project.

