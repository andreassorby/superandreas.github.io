# Installation Guide - Simple Media Encoder

## System Requirements

- **macOS**: 14.0 or later
- **Architecture**: Intel x86_64 or Apple Silicon (M1/M2/M3)
- **Memory**: 4GB RAM minimum, 8GB recommended for large files
- **Storage**: 100MB free space for app + conversion outputs
- **Xcode**: 15.0 or later (only for building from source)

## Installation Methods

### Option 1: Download Release Binary (Recommended)

1. **Download**: Go to [GitHub Releases](https://github.com/andreassorby/simple-media-encoder/releases)
2. **Get Latest**: Download `SimpleMediaEncoder.zip` from the latest release
3. **Extract**: Unzip the downloaded file
4. **Run**: Double-click `SimpleMediaEncoder` or run from Terminal

### Option 2: Build from Source

#### Quick Build
```bash
# Clone the repository
git clone https://github.com/andreassorby/simple-media-encoder.git
cd simple-media-encoder

# Build v1.0
cd v1.0
chmod +x build.sh
./build.sh

# Launch
./SimpleMediaEncoder &
```

#### Build Script Details
The `build.sh` script compiles the Swift source with these frameworks:
- SwiftUI (UI framework)
- AVFoundation (audio processing)
- AppKit (macOS integration)
- UniformTypeIdentifiers (file type handling)

### Option 3: Development Setup

For contributors and developers:

```bash
# Clone with full history
git clone https://github.com/andreassorby/simple-media-encoder.git
cd simple-media-encoder

# Check project structure
ls -la v1.0/
ls -la test_files/input/

# Build and test
cd v1.0
./build.sh
./SimpleMediaEncoder &

# Test with sample file
# Drag test_files/input/test_audio.mp3 into the app
```

## Verification

### Test Installation
1. **Launch** the app: `./SimpleMediaEncoder &`
2. **Drag & Drop**: Drag `test_files/input/test_audio.mp3` into the app window
3. **Select Format**: Choose AIFF output format
4. **Convert**: Click "Convert Files" and select output directory
5. **Verify**: Check that conversion completes successfully

### Expected Output
```
📥 Processing dropped files...
✅ Added: test_audio.mp3 (MP3 Audio)
🗂️ Opening folder picker...
✅ Output directory set to: /path/to/output
🎯 Starting Ultimate Conversion:
   Format: AIFF
   Sample Rate: 44.1 kHz
   Bit Depth: 16-bit
   Channels: Stereo
🎵 Converting 1/1: test_audio.mp3
✅ Conversion pipeline completed successfully
✅ Success: XX.X MB
```

## Troubleshooting

### Build Issues

**Problem**: `swiftc: command not found`
**Solution**: Install Xcode Command Line Tools:
```bash
xcode-select --install
```

**Problem**: Framework not found errors
**Solution**: Ensure macOS 14.0+ and Xcode 15.0+:
```bash
swift --version
```

**Problem**: Permission denied on build.sh
**Solution**: Make script executable:
```bash
chmod +x build.sh
```

### Runtime Issues

**Problem**: App won't launch - "damaged and can't be opened"
**Solution**: Remove quarantine attribute (macOS security):
```bash
xattr -d com.apple.quarantine SimpleMediaEncoder
```

**Problem**: Conversion fails with error
**Solution**: Check input file format is MP3 and readable:
```bash
file test_audio.mp3
ls -la test_audio.mp3
```

**Problem**: GUI appears but is unresponsive
**Solution**: Ensure sufficient system resources and close other apps

### Performance Issues

**Problem**: Slow conversion speed
**Solution**: 
- Close other resource-intensive applications
- Use smaller input files for testing
- Check available disk space in output directory

**Problem**: High memory usage
**Solution**: Process files individually instead of batch processing

## Uninstallation

Simple Media Encoder is a single binary with no system dependencies:

1. **Delete Binary**: Remove the `SimpleMediaEncoder` file
2. **Clean Outputs**: Optionally delete converted files
3. **Remove Source**: Delete the project directory if built from source

## Security Notes

- App requests file system access for reading input files
- App requests file system access for writing output files  
- No network access required or requested
- No data collection or telemetry
- All processing happens locally on your Mac

## Next Steps

- **Usage Guide**: See [usage.md](usage.md) for detailed feature documentation
- **Development**: See [development.md](development.md) for contribution guidelines
- **Support**: Open issues on [GitHub](https://github.com/andreassorby/simple-media-encoder/issues) 