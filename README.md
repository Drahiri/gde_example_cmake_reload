# GDExample with CMake hot-reload

[GDExtension C++ example](https://docs.godotengine.org/en/stable/tutorials/scripting/gdextension/gdextension_cpp_example.html) using CMake with hot reloading enabled.

## Instruction

1. Clone repository and enter it.

```
git clone https://github.com/Drahiri/gde_example_cmake_reload.git
cd gde_example_cmake_reload
```

2. Initialize godot-cpp submodule.

```
cd godot-cpp
git submodule update --init
```

3. Add following lines to `godot-cpp/CMakeLists.txt` at line `129` to match [this PR](https://github.com/godotengine/godot-cpp/pull/1548/files).

```cmake
if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    set(GODOT_COMPILE_FLAGS "${GODOT_COMPILE_FLAGS} -fno-gnu-unique")
endif()
```

4. Leave `godot-cpp` folder.

```
cd ..
```

5. Create `build` folder, configure and build project. `x` is number of jobs.

```
mkdir build
cd build
cmake .. -GNinja
ninja -jx
```

6. Import and open demo project in Godot.

7. Make changes in `gdexample.cpp` file. Commenting out `_bind_methods()` content is good idea.

8. Rebuild library.

9. If you commented out `_bind_methods()` content, in editors' Inspector property `Amplitude` should disappear.
