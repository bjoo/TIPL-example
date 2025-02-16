## Introduction

Template Image Processing Library (TIPL) is a lightweight C++ template library designed mainly for medical imaging processing. The design paradigm is to provide an "easy-to-use" and also "ready-to-use" library. You need only to include the header files to use it. There is no need to build the source codes.

##Design paradigm

A lot of the image processing libraries are designed for experimental/research purposes and do not meet the industrial standard. Consequently, the performance of the codes is not optimal, and the library can be hard to read and use. The design of TIPL follows several coding guidelines and principles that make it highly efficient and reusable. The following is the main paradigm behind TIPL.

- Decouple image type and image processing method. Most of the image processing libraries are limited to their defined image type. TIPL is not. You may use a pointer or any kind of memory block to as the input. This reduces unnecessary memory storage and copy.

- Not limited to RGB pixel type. In medical imaging, the most common pixel type is "short" or "float", not the RGB value. TIPL makes no assumption on the pixel type to achieve the best applicability..

- No class inheritance, no hidden functions or interfaces. Class inheritance is known to cause programs in code maintenance and it is not friendly for library users to customize the library. TIPL combines template-based interfaces with C-style interfaces to provide a "flat" library structures that is easy to maintain and modify. The connections between header files are thereby minimized. 


## Installation

1. Get header files from Github

```
!git clone http://github.com/frankyeh/TIPL/
```

2. Include the header 

```
#include "TIPL/tipl.hpp"  
```

Now you can use TIPL

### Building the C++ examples using CMake

It is possible to install TIPL using CMake, in which case C++ packages using CMake can easily build with it. 
In this package C++ examples are available in the `cpp` subdirectory. To build these using CMake:

* Make sure TIPL is installed with CMake, e.g. in a directory called `<TIPL_install_directory>`  (see the TIPL README.md file how to do this).
* Execute the commands from the root of your cloned `TIPL-example` directory:
```bash$
export CMAKE_PREFIX_PATH=<TIPL_install_directory>:$CMAKE_PREFIX_PATH
mkdir build ; cd build
cmake ..
cmake --build .
cd cpp
```
* At this point one should be able to execute the exmaple, e.g.:
```bash$
./linear_reg
```
* We also made a directory `cpp/TIPL-examples` and symbolic linked the source `data` directory there so that the exmaples can find their inputs.

Naturally one can also locate the CMake TIPLConfig.cmake file using other CMake means than `CMAKE_PREFIX_PATH` e.g. by providing the CMake option: `-DTIPL_DIR=<TIPL_install_directory>/lib/cmake/TIPL` to cmake. One should also be able to build out of source (the `build` directory can really be anywhere). 

Installation of the examples is not yet supported

## Example

- Notebooks examples:
  - Image IO [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/frankyeh/TIPL-example/main?filepath=/image_io.ipynb)
  - Volume and Slicer Operations [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/frankyeh/TIPL-example/main?filepath=/volume_slice_operations.ipynb)
  - Pixel Operations (Filters) [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/frankyeh/TIPL-example/main?filepath=/pixel_operations.ipynb)
  - Morphological Operations [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/frankyeh/TIPL-example/main?filepath=/morphology_operations.ipynb)
  - NIFTI file viewer [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/frankyeh/TIPL-example/main?filepath=/nifti_viewer.ipynb)

- Google colab examples:
  - Load NIFTI file [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/frankyeh/TIPL-example/blob/main/colab/load_nii.ipynb)
  - Image registration [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/frankyeh/TIPL-example/blob/main/colab/linear_reg.ipynb)
