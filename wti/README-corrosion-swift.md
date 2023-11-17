# Eclipse Corrosion IDE integration as template for swift on eclipse
- My current swift-lsp has only: LSP, highlighting, run
- This adds project and debugger support for rust, tracks multiple eclipse versions, and should build.
- If working, consider as template for swift on Eclipse

## Status
- Approach
    - Get corrosion fully working in CLI and eclipse: build, test, and run based on this code
    - Evaluate work for Swift:
        - Debugger support based on corrosion's
        - LSP (swift-syntax) outline, augmented analysis
- Corrosion itself now not working d/t gdb install?
- CLI build and application works, but tests fail and no debugging

## Configuration
- CLI builds require maven 
- Application and tests require a standard (rustup) install
- Running application/plugin requires eclipse CDT-gdb support?
    - Which seems to only work for gcc gdb

### Source 
- Checkout from repo

### Build on command line
- `mvn verify >| org.eclipse.corrosion.out.tmp.txt`

### Install rust
- `brew install rustup`
- `rustup-init`
    - Targets `~/.cargo`
    - Expecting executables: rustup, rustc, cargo, rust-analyzer (lsp)
    - Configure PATH to put first `~/.cargo/bin`?

### Install CDT
- marketplace: Seek CDT, perhaps CMake editor
- Configure CDT (in eclipse settings) (including CMake toolchains?)
    - untested: [ios-cmake toolchains file also supports macos](https://github.com/leetal/ios-cmake)
- new-project wizard only support gcc toolchains; I have only xcode for now
    - Unclear if any support CMake

### Import sources into eclipse 
- Import target platform project and set as active target
- Import corrosion and test project

### debugging: Use gdb?
- need to install

### debugging: use lldb?
- [lldb support in eclipse is hanging](https://discourse.llvm.org/t/can-window-eclipse-use-lldb-debug/66226)
    - [lldb-mi - eclipse interface to lldb low-traffic but active](https://github.com/lldb-tools/lldb-mi)

