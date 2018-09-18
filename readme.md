# How to use Eigen3 with CMake

## instllation of Eigen3 library

1. Download it from [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page);
2. Unzip it and create the `build` directory in the folder of the source folder;
3. Run cmake with `cmake -G "MinGW Makefiles" ../ -DCMAKE_INSTALL_PREFIX=/path/to/installation/folder`;
4. Run make with `make install`;
5. Locate the headers of `Eigen` and the `cmake` configuration files located at the installation folder.

## Usage the `Eigen` library with cmake

1. Create a folder of `cmake` at the root directory of your source code;
2. Copy the configuration files of `Eigen` to the directory so-called `cmake`;
    ```
    ./
    ./main.cpp
    ./CMakeLists.txt
    ./cmake/
    ./cmake/Eigen3Config.cmake
    ./cmake/Eigen3ConfigVersion.cmake
    ./cmake/Eigen3Targets.cmake
    ./cmake/UseEigen3.cmake
    ```
3. Configure your `CMakeLists.txt`;
    ```
    cmake_minimum_required (VERSION 3.0)
    project (Name_Of_Your_Project)

    # important setting for accessing the eigen library
    list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
    find_package(Eigen3 REQUIRED)
    include_directories(${EIGEN3_INCLUDE_DIR})

    message("${CMAKE_MODULE_PATH}")
    message("${EIGEN3_INCLUDE_DIR}")

    add_executable (executable main.cpp)

    target_link_libraries(executable 
        PUBLIC
            Eigen
    )
    ```
4. Make a build directory namely `build` and change the working directory into that folder;
5. Run the `cmake` with `cmake -G "MinGW Makefiles" ../ -DCMAKE_PREFIX_PATH=/path/to/installation/folder`;
    *Note* It is worthy of noting that the `CMAKE_PREFIX_PATH` is the same as that of `-DCMAKE_INSTALL_PREFIX`.
5. Run `make` with `make -j2`.