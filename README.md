
# CUDA Utilities and Gaussian Blur

This repository contains CUDA utility functions for device detection, memory allocation, and image processing. Additionally, it includes an implementation of a CUDA-based Gaussian blur applied to an input image.

## Directory Structure

```
└── ./ 
    └── src
        ├── cudautils_devices.cpps
        ├── cudautils_memory.cpp
        └── main.cpp
```

### File Descriptions

1. **`/src/cudautils_devices.cpp`**  
   Contains functions for detecting CUDA capable devices and checking the properties of these devices. The `findCapableDevice()` function is used to identify the best available CUDA device based on its capabilities.

2. **`/src/cudautils_memory.cpp`**  
   Provides functions for managing memory allocation on the GPU. It includes template functions for allocating and downloading memory from the device, as well as for creating CUDA arrays and uploading images to textures and surfaces.

3. **`/src/main.cpp`**  
   Contains the main application logic. It uses OpenCV for image loading and processing, and applies a CUDA-based Gaussian blur to an input image. The processed image is either displayed on the screen or saved to the specified output file.

## Prerequisites

- CUDA Toolkit (version 8.0 or higher recommended)
- OpenCV
- Qt Framework (for command-line parsing)

## Compilation and Execution

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/kamlesh364/cuda-utils.git
   cd cuda-utils
   ```

2. Set up the build environment (ensure that you have a compatible version of CUDA installed):
   ```bash
   cmake .
   make
   ```

3. Run the application with an input image:
   ```bash
   ./main <input_image_path> -o <output_image_path>
   ```

   - `<input_image_path>`: Path to the input image to be processed.
   - `-o <output_image_path>`: Optional argument to save the output image to a file.

4. If no output path is provided, the processed image will be displayed in a window.

## Functions

- **`findCapableDevice()`**: Finds and sets the best available CUDA device based on device capabilities.
- **`allocateDeviceMem<T>()`**: Allocates memory on the GPU for different data types (uchar, int, float, etc.).
- **`downloadArray<T>()`**: Downloads data from device memory to host memory.
- **`downloadArrayToImage<T>()`**: Downloads data from device memory to a cv::Mat image.
- **`uploadImageToTexture<T>()`**: Uploads an image to a CUDA texture.
- **`runCudaGaussianBlur()`**: Applies a Gaussian blur on the input image using CUDA.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
