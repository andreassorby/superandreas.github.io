# Development Guide - Simple Media Encoder v2.4

## Architecture Overview

Simple Media Encoder follows a modular SwiftUI architecture with clear separation of concerns:

### Core Components

```
v2.0-dev/
├── Sources/
│   ├── ConversionEngine/     # Media processing logic
│   ├── UserInterface/        # SwiftUI views and components
│   └── Utilities/           # Helper functions and extensions
└── Tests/                   # Unit and integration tests
```

### Key Classes

- **`SimpleMediaEncoderApp`**: Main app entry point with window management
- **`ContentView`**: Primary UI with file selection and conversion controls
- **`PresetStore`**: Centralized preset management with ObservableObject
- **`AudioConverter`**: AVFoundation-based audio processing
- **`VideoConverter`**: AVAssetExportSession-based video processing
- **`MediaFile`**: Data model for input/output file handling

## Development Philosophy

### Working-First Approach
- **Proven Logic**: Always start with working conversion engines
- **Incremental Changes**: Small, testable modifications
- **Backup Strategy**: Preserve working versions in `/backups`
- **Real Testing**: Use actual media files, not synthetic data

### Swift 6 Concurrency
- **Async/Await**: All media processing uses modern concurrency
- **@MainActor**: UI updates properly isolated
- **@preconcurrency**: Suppress AVFoundation warnings
- **Sendable**: Proper thread safety for shared data

## Code Standards

### Swift Style
```swift
// Preferred: Clear, descriptive names
func convertAudioFile(from inputURL: URL, to outputURL: URL) async throws

// Avoid: Abbreviated or unclear names
func conv(f: URL, t: URL) async throws
```

### Error Handling
```swift
// Comprehensive error handling
enum ConversionError: LocalizedError {
    case inputFileNotFound
    case outputLocationNotWritable
    case unsupportedFormat
    case conversionFailed(String)
    
    var errorDescription: String? {
        switch self {
        case .inputFileNotFound: return "Input file not found"
        // ... other cases
        }
    }
}
```

### UI Patterns
```swift
// Semantic colors for dark mode
Color(NSColor.controlBackgroundColor)  // ✅ Adapts to theme
Color.white                            // ❌ Hardcoded

// Proper state management
@StateObject private var presetStore = PresetStore()  // ✅ Single source
@State private var presets = [Preset]()               // ❌ Duplicated state
```

## Building and Testing

### Development Build
```bash
cd v2.0-dev
swift build -c debug
swift run SimpleMediaEncoder
```

### Release Build
```bash
swift build -c release
swift package archive --output-path ./build
```

### Running Tests
```bash
# All tests
swift test

# Specific test suite
swift test --filter ConversionEngineTests

# With real media files
./scripts/test.sh
```

### Test Files
Use consistent test files in `/test_files/input/`:
- `test_audio.mp3` - Standard audio test
- `test_video.mp4` - Standard video test
- `01 Frihet.wav` - High-quality audio sample

## Common Development Tasks

### Adding New Audio Format
1. Update `AudioTypes.swift` with new format enum
2. Add conversion logic to `AudioConverter.swift`
3. Update UI format picker in `ContentView.swift`
4. Add tests with real files
5. Update documentation

### Creating New Preset
```swift
// In PresetStore.swift
let newPreset = AudioPreset(
    name: "Custom Quality",
    format: .mp3,
    codec: .mp3,
    bitrate: 192,
    sampleRate: 44100
)
presetStore.addPreset(.audio(newPreset))
```

### Debugging Conversion Issues
1. Enable verbose logging in conversion engine
2. Check input file with `ffprobe` or similar
3. Verify output directory permissions
4. Test with minimal conversion parameters
5. Compare with working backup version

## Memory Management

### AVFoundation Objects
```swift
// Proper cleanup
defer {
    reader.cancelReading()
    writer.cancelWriting()
}
```

### Large File Handling
```swift
// Process in chunks
let bufferSize = 4096
while let buffer = reader.copyNextSampleBuffer() {
    // Process buffer
    // Release immediately
}
```

## UI Development

### SwiftUI Best Practices
```swift
// Computed properties for complex UI
var formatPicker: some View {
    Picker("Format", selection: $selectedFormat) {
        ForEach(AudioFormat.allCases, id: \.self) { format in
            Text(format.displayName).tag(format)
        }
    }
}

// Environment objects for shared state
@EnvironmentObject var presetStore: PresetStore
```

### Window Management
```swift
// Force window to front (macOS specific)
NSApp.setActivationPolicy(.regular)
NSApp.activate(ignoringOtherApps: true)
```

## Performance Optimization

### Conversion Pipeline
- Use background queues for media processing
- Implement proper cancellation for long operations
- Monitor memory usage during batch conversions
- Cache frequently used conversion settings

### UI Responsiveness
- Keep UI updates on main thread
- Use `@Published` for reactive updates
- Debounce rapid user input
- Show progress indicators for long operations

## Debugging Tools

### Xcode Instruments
- **Time Profiler**: Identify performance bottlenecks
- **Allocations**: Monitor memory usage
- **System Trace**: Understand thread behavior

### Console Logging
```swift
// Structured logging
os_log("Conversion started: %@", log: .conversion, type: .info, inputURL.path)
os_log("Conversion failed: %@", log: .conversion, type: .error, error.localizedDescription)
```

### AVFoundation Debugging
```swift
// Check asset properties
let asset = AVAsset(url: inputURL)
print("Duration: \(asset.duration)")
print("Tracks: \(asset.tracks.count)")
```

## Release Process

### Version Bumping
1. Update version in `Package.swift`
2. Update `CHANGELOG.md`
3. Update documentation
4. Tag release: `git tag v2.4.0`

### Quality Checklist
- [ ] All tests pass
- [ ] Manual testing with various file types
- [ ] UI works in light and dark modes
- [ ] Memory leaks checked with Instruments
- [ ] Performance acceptable on older hardware
- [ ] Documentation updated

### Distribution
```bash
# Create release archive
./scripts/release.sh

# Generate checksums
shasum -a 256 SimpleMediaEncoder-v2.4.zip
```

## Troubleshooting Development Issues

### Build Errors
- **Package.swift not found**: Ensure you're in `v2.0-dev` directory
- **Module not found**: Check import statements and dependencies
- **Concurrency warnings**: Add `@preconcurrency` imports

### Runtime Issues
- **App won't launch**: Check permissions, code signing
- **Conversion hangs**: Verify AVFoundation setup, check for deadlocks
- **UI not updating**: Ensure `@Published` properties and main thread updates

### Git Workflow
```bash
# Feature development
git checkout -b feature/new-format-support
# ... make changes
git commit -m "Add FLAC format support"
git push origin feature/new-format-support
# Create pull request
```

## Contributing Guidelines

### Code Review
- All changes require testing with real media files
- Performance impact must be considered
- UI changes need dark mode verification
- Documentation updates required for new features

### Pull Request Template
```markdown
## Description
Brief description of changes

## Testing
- [ ] Tested with audio files
- [ ] Tested with video files  
- [ ] Tested in dark mode
- [ ] Performance impact assessed

## Checklist
- [ ] Code follows style guidelines
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] Changelog updated
```

This development guide ensures consistent, high-quality contributions to Simple Media Encoder while maintaining the working-first philosophy that has made the project successful. 