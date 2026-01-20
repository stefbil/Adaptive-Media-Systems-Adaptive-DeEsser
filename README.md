# Adaptive DeEsser

This project is part of the Adaptive Media Systems course of the Medialogy MSc program at Aalborg University in Copenhagen, Denmark.
Author: Stefanos Biliousis
Supervisor: Cumhur Erkut

---

This plugin is designed to transparently reduce sibilance in vocal recordings using adaptive frequency detection and high-quality filtering.

## Features

*   **Adaptive Frequency Detection**: Automatically detects and tracks sibilant frequencies for more natural de-essing.
*   **Real-Time Visualization**:
    *   **Waveform Scope**: Visual feedback of the input signal and gain reduction.
    *   **FFT Spectrum Analyzer**: High-resolution spectral analysis to identify problem frequencies.
*   **Dual-Band Processing**: Uses high-quality crossovers to split the signal, applying processing only to the sibilant high frequencies while preserving the body of the vocal.
*   **Parametric Mode**: (Internal) Specialized filtering options for precise control.
*   **Zero Latency**: (Depending on configuration) Optimized for real-time tracking and mixing.

## Requirements

*   **JUCE Framework**: This project depends on JUCE. Ensure you have the global JUCE modules available or configured via CMake/Projucer.
*   **CMake**: Version 3.15 or higher.
*   **C++ Compiler**: C++17 compliant compiler (MSVC, Clang, GCC).

## Building

### Using CMake

The `CMakeLists.txt` is currently configured to look for the JUCE library in the parent directory (`../JUCE`).

1.  Ensure you have the JUCE framework located at `../JUCE` relative to this repository.
    *   *Alternatively, edit `CMakeLists.txt` to point to your specific JUCE installation path.*

2.  Configure and build:
    ```bash
    cmake -B build
    cmake --build build --config Release
    ```

3.  To clean the build:
    ```bash
    cmake --build build --target clean
    ```

    *   *TODO: Make CMake and Projucer use the same Build folder.*

### Using Projucer

1.  Open `Adaptive DeEsser.jucer` in the Projucer application.
2.  Verify the "Global Paths" module settings match your local JUCE installation.
3.  Save the project to generate the IDE project files (Visual Studio, Xcode, Makefile, etc.).
4.  Open the generated project file and build the `VST3` or `AU` target.

#### macOS Specifics (Projucer)

If you are on macOS and using Projucer from the command line:

```bash
# Generate Xcode project
../JUCE/Projucer.app/Contents/MacOS/Projucer --resave "Adaptive DeEsser.jucer"

# Build
xcodebuild -project "Builds/MacOSX/Adaptive DeEsser.xcodeproj"

# Verify standalone app
open "Builds/MacOSX/build/Debug/Adaptive DeEsser.app"
```

## Usage

1.  Load the plugin on a vocal track in your DAW.
2.  Adjust the **Threshold** to catch the "S" sounds.
3.  Use the **Frequency** control (or enable Auto mode) to target the harsh frequencies.
4.  Monitor the **Scope** and **Spectrum** to visualize the reduction.

## Testing

TODO: Add a simple vocal file or grab it.

## License

This project is licensed under the [Apache-2.0 License](LICENSE).
