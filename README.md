# GPU-path-tracing-tutorial-4
Matching Socks CUDA path tracer
by Samuel Lapere, 2016
https://raytracey.blogspot.com

Screenshots and more info about this tutorial can be found at http://raytracey.blogspot.co.nz/2016/09/gpu-path-tracing-tutorial-4-optimised.html

Demo of high performance CUDA accelerated path tracing
based on the GPU ray tracing framework of Timo Aila, 
Samuli Laine and Tero Karras (Nvidia Research)

Source code for original framework: 
- https://code.google.com/archive/p/understanding-the-efficiency-of-ray-traversal-on-gpus/
- https://research.nvidia.com/publication/understanding-efficiency-ray-traversal-gpus-kepler-and-fermi-addendum
- https://mediatech.aalto.fi/~timo/HPG2009/

Features:

- fast interactive path tracing
- progressive rendering
- interactive camera and depth-of-field
- real-time user interaction
- BVH acceleration structure built with surface area heuristic (SAH) and spatial splits
- Woop ray/triangle intersection
- highly optimised hand tuned ray traversal and intersection kernels
- HDRI environment mapping
- anti-aliasing
- basic OBJ loader
- basic material system with support for diffuse, clearcoat, refractive (glass), specular(mirror) and metal material
- support for spheres and triangle meshes


Downloadable demo available at 
https://github.com/straaljager/GPU-path-tracing-tutorial-4/releases


Instructions for compiling with Visual Studio 2013/2015:

- download and install the CUDA 7.5 toolkit and choose integration with Visual Studio
- open VS2013/2015 (Express or any other version such as the free Community version)
- click New Project...
- select Visual C++, then General, then Empty Project
- right click on the project, select Build Dependies > Build Customizations
- select the CUDA 7.5 checkbox, click OK
- add all the files to the project
- in the project explorer window, right click on render_kernel.cu file, select Properties, change the Item type to CUDA C/C++
- right click on the project name, select Properties
- under Linker > Input > Additional Dependencies, add "cudart.lib" and "glew32.lib" (glew32.lib should be automatically found when the CUDA toolkit is installed) 
- when the compiler can't find glew32.lib, add the library path to Linker > General > Additional Library Directories, the path is something like "%NVSDKCOMPUTE_ROOT%\C\common\lib")
- disable SAFESEH by selecting NO in Linker > Advanced > Image Has Safe Exception Handlers
- select Build > Rebuild Solution and run the program 

Issues:

- the OBJ loader is quite basic at the moment and only loads obj models that are in a particular format, hence some but not all OBJ files will work
- at the moment there is no CUDA error checking when copying data to the GPU, if model or HDR map data is missing, not found or not in the right format, the program will exit or display a black screen


