This repository contains source codes of the actual implementation described in the paper,

<a href=https://ieeexplore.ieee.org/document/9578988>S. Lee, H. Jung and C. E. Rhee, "Data Orchestration for Accelerating GPU-Based Light Field Rendering Aiming at a Wide Virtual Space," in _IEEE Transactions on Circuits and Systems for Video Technology_, vol. 32, no. 6, pp. 3575-3586, June 2022.</a>

----

This is a demo version and may contain bugs. Light field data is required to run this program, but it is 
not included here. We will provide it ASAP.

Also, you can watch the demo video through the following url: : https://www.youtube.com/watch?v=lrIsEJbiGNg

Project Environment : C++ 17, MSVC v142.

Dependencies : CUDA 11.2, GLEW, freeglut

-----

**expore-virtual-space**

- **README.md** : This file

- **INTRODUCTION.md** : Introduction to what we did

- **/data** 

  - **LFdata** (Not prepared yet)
    Light field data we acquired. Captured at the "BMW Driving Center" in Incheon, Korea. Thanks again for the rental of the place.
  - **pixel_selection**
    Pre-calculated pixel-selection range based on Light-field theory. Each text file name represents user's location inside the LFU. For example, 50_50 means (x, y) = (50, 50).
    You can choose between two resolutions: 4096x2048 and 7680x4320.
  - **Map configuration_BMW driving center_Incheon_Korea.xlsx** 
    Index information of the light field data constituting the virtual space of 600x5600 cm<sup>2</sup>. 

- **/sources**
  
  Including source codes. Import these files into your project. You should replace three macros, RESOLUTION, PATH_LF, and PATH_PIXEL_RANGE. RESOLUTION represents the resolution specification of Light-field data that you use (But now, we only support 4K and 8K). PATH_LF and PATH_PIXEL_RANGE should be set to your directory path where you save the Light-field data and pixel_selection data, respectively.
  
  ```c++
    #define RESOLUTION ${YOUR_RESOLUTION_SPECS}
    ...
    #define PATH_LF ${YOUR_LF_DIRECTORY_PATH}
    #define PATH_PIXEL_RANGE ${YOUR_PIXEL_SELECTION_PATH}
  ```
  
  ***NOTE:*** The last argument among the constructors of the `LF_Renderer` class determines whether to use the LFU window mode or explore only inside a single LFU. 
  
  ```c++
    LF_Renderer renderer(PATH_LF, PATH_PIXEL_RANGE, WIDTH, HEIGHT, LF_length, num_LFs, dpp, stride, curPosX, curPosY, true);
  ```

- **lib/bin**

  libs and dlls for glew and freeglut.

