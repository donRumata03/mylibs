# Pythonic
It\`s a C++ library which provides basic functions simplifying all aspects of work
I use it in all of my C++ projects and it\`s absolutely irreplaceable for me.

## Usage:
This library uses CMake as build system.
To use this library you probably need to build it for you platform and compiler. 
However, there are some binary files in "cmake-build-debug" and "cmake-build-release" (.exe and .lib)

There are no additional dependencies, so, you should simply run CMake.
After that, *.lib files for Release or Debug mode appear in the corresponding locations.
To use it from other libraries or executables you should type 
    `set(Pythonic_DIR ${LOCATION_OF_THE_ROOT_FOLDER_OF_PYTHONIC})`
in you CMake file. And after that:
    `find_package(Pythonic required)` 

"pythonic_static_library" variable will contain the name of the library you should link against.
"pythonic_include_directories" variable will contain the list of directories you should add to you include directory index.

So, you should write this lines:

    include_directories(${pythonic_include_directories})
    target_link_libraries(${YOUR_TARGET_NAME} ${pythonic_static_library})


## Features:
- Utilities for displaying (in "./displaying/" folder):
    - STL containers stream output operators
    - Type name getter function, returns std::string, pays respect to pointers, references, specifiers and qualifiers
    - ANSI colors in console (see https://en.wikipedia.org/wiki/ANSI_escape_code)
    - Some library from github, which displays a number of bytes in human readable format and supports different standards

- Some primitives for geometry (in "./geometry/" folder):
    - Point: has stream output operator and other stuff
    - Line (has support of different formats for representing a line)
    - Circle : also supports different formats including "three points" format
    
- Multidimensional Array class with slicing support (see n_dim/nd_array.h):
    - // TODO: write some useful characters here!
    
- A collection of random generators:
    - Random number from [0, 1) with rand() and with std::mt19937
    - Random number from [x, y) with rand() and with std::mt19937
    - Choice a random element of a collection
    - Normalizer: a class which applies a hack to speed the generation of normal distributed random numbers up: it generates a number of them at the initialization and when a random number with a given σ and μ is required, it applies some linear transformations and outputs the result. It\`s possible to tune the precision and memory consumption by changing the number of the generated randoms
    - "probability_choose" function chooses one or more (depending on its argument)

- Tools to deal with encodings (in "./encoding/" folder):
    - My C++ wrapper around WinAPI for converting between UTF-8, UTF-16 (windows system encoding), and CP-1251 (one-byte cyrillic encoding)
    - Automatic encoding determination (UTF-8, CP-1251 and pure ASCII)
    - Automatic recoding to one of those encodings (UTF-8, CP-1251 and pure ASCII)
- Utilities to deal with letters: determines if a character is russian, english, space, digit. e.t.c. assumes that the character represents a cp1251-encoded code unit


All of the features ^^^ above ^^^ are covered by tests (in folder with corresponding name)

Feel free to contact me if there are some issues with understanding the library interface or even bugs: donrumata03@gmail.com
