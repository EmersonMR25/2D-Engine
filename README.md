# 2D Game Engine

This project is a cross-platform 2D game engine developed in C++17, utilizing [raylib](https://www.raylib.com/) for graphics and [raygui](https://github.com/raysan5/raygui) for GUI components. The build system is managed with CMake, ensuring compatibility with macOS, Windows, and Linux.

## Features

- **Cross-Platform**: Build and run on macOS, Windows, and Linux.
- **Modern C++17**: Leverage the features and robustness of C++17.
- **Simple Integration**: Utilize raylib and raygui for graphics and GUI, respectively.
- **CMake Build System**: Streamlined building and dependency management.

## Requirements

- **C++17 Compiler**: Ensure you have a compiler that supports C++17.
- **CMake**: Version 3.0 or higher is required.
- **Git**: For cloning the repository and managing submodules.

## Dependencies

- **raylib**: A simple and easy-to-use library to enjoy videogames programming.
- **raygui**: A simple and easy-to-use immediate-mode GUI library.

These dependencies are included as submodules in this project.

## Getting Started

### Clone the Repository

```bash
git clone --recursive https://github.com/EmersonMR25/2D-Engine.git
cd 2D-Engine
```

If you have already cloned the repository without submodules, initialize them with:

```bash
git submodule update --init --recursive
```

### Build Instructions

1. **Create a Build Directory**:

   ```bash
   mkdir build
   cd build
   ```

2. **Configure the Project with CMake**:

   ```bash
   cmake ..
   ```

   - For a specific build type (e.g., Release):

     ```bash
     cmake .. -DCMAKE_BUILD_TYPE=Release
     ```

3. **Build the Project**:

   - On Unix-like systems (macOS/Linux):

     ```bash
     make
     ```

   - On Windows with Visual Studio:

     ```bash
     cmake --build . --config Release
     ```

### Running the Engine

After a successful build, the executable will be located in the `build` directory. Run it with:

```bash
./2D-Engine
```

On Windows:

```bash
2D-Engine.exe
```

## Platform-Specific Notes

- **macOS**: Ensure you have the necessary development tools installed, such as Xcode Command Line Tools.
- **Windows**: It's recommended to use Visual Studio or MinGW for building the project.
- **Linux**: Install the essential build tools and libraries using your distribution's package manager.

## License

This project is licensed under the [MIT License](LICENSE).

---

For more information on raylib and raygui, refer to their official documentation:

- raylib: [https://www.raylib.com/](https://www.raylib.com/)
- raygui: [https://github.com/raysan5/raygui](https://github.com/raysan5/raygui)

---