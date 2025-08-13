# Simple Media Encoder v2.4

A powerful, native macOS media conversion application built with Swift 6 and SwiftUI. Convert audio and video files with professional-grade quality and extensive format support.

## Features

### Core Conversion
- **Audio Conversion**: MP3, AAC, FLAC, WAV, AIFF, OGG, M4A
- **Video Conversion**: MP4, MOV, AVI, MKV, WebM, FLV
- **Batch Processing**: Convert multiple files simultaneously
- **Quality Control**: Bitrate, sample rate, and codec customization
- **Progress Tracking**: Real-time conversion progress with time estimates

### Advanced Features
- **Preset Manager**: 15 built-in presets plus custom preset creation
- **Finder Integration**: Right-click context menu for quick conversions
- **Settings Management**: Persistent settings with import/export
- **Dark Mode Support**: Native macOS appearance adaptation
- **Menu Bar Integration**: Quick access to settings and presets

### User Interface
- **Native macOS Design**: SwiftUI with native controls and animations
- **Drag & Drop**: Intuitive file selection
- **Multi-Window Support**: Open multiple conversion windows
- **Responsive Layout**: Adapts to window resizing
- **Professional Branding**: Custom app icon and color scheme

## Installation

### Quick Start
1. Download the latest release from GitHub
2. Extract and run the application
3. Grant necessary permissions for file access

### Building from Source
```bash
# Clone repository
git clone https://github.com/yourusername/Simple_media_encoder.git
cd Simple_media_encoder

# Build and run
./launch.sh

# Or build manually
cd v2.0-dev
swift build
swift run SimpleMediaEncoder
```

## Usage

### Basic Conversion
1. Launch Simple Media Encoder
2. Click "Select Files" or drag files into the window
3. Choose output format and quality settings
4. Click "Convert" to start processing

### Preset Manager
- **Access**: Settings → Preset Manager
- **Built-in Presets**: 15 professional presets for common use cases
- **Custom Presets**: Create and save your own conversion settings
- **Editing**: Modify any preset (name, format, codec, quality)
- **Synchronization**: Changes sync instantly with main window

### Finder Integration
1. Right-click any media file in Finder
2. Select "Services" → "Convert with Simple Media Encoder"
3. File opens directly in the application

### Settings
- **General**: Default output location, naming patterns
- **Audio**: Default codecs, quality settings, sample rates
- **Video**: Encoding presets, resolution options, frame rates
- **Advanced**: Custom ffmpeg parameters, logging options

## Supported Formats

### Audio Input
- MP3, AAC, FLAC, WAV, AIFF, OGG, M4A, WMA, APE, OPUS

### Audio Output
- **MP3**: 32-320 kbps, VBR support
- **AAC**: 64-256 kbps, HE-AAC support
- **FLAC**: Lossless compression
- **WAV**: Uncompressed PCM
- **AIFF**: Apple's uncompressed format
- **OGG**: Open-source alternative

### Video Input
- MP4, MOV, AVI, MKV, WebM, FLV, WMV, 3GP, M4V

### Video Output
- **MP4**: H.264/H.265, multiple quality profiles
- **MOV**: QuickTime format, professional codecs
- **WebM**: VP8/VP9 for web optimization
- **AVI**: Legacy format support

## Keyboard Shortcuts

- **⌘O**: Open files
- **⌘N**: New window
- **⌘W**: Close window
- **⌘,**: Open settings
- **⌘R**: Start conversion
- **⌘.**: Cancel conversion
- **⌘⇧P**: Open Preset Manager

## Technical Details

### Architecture
- **Framework**: SwiftUI with Combine for reactive programming
- **Conversion Engine**: AVFoundation with custom processing pipeline
- **Concurrency**: Swift 6 async/await for responsive UI
- **Storage**: UserDefaults for settings, file-based preset management

### Performance
- **Multi-threading**: Parallel processing for batch conversions
- **Memory Management**: Efficient buffer handling for large files
- **Progress Tracking**: Real-time updates without blocking UI
- **Error Handling**: Comprehensive error reporting and recovery

### System Requirements
- **macOS**: 12.0 (Monterey) or later
- **Architecture**: Apple Silicon (M1/M2) and Intel
- **Memory**: 4GB RAM minimum, 8GB recommended
- **Storage**: 100MB free space for application

## Troubleshooting

### Common Issues
- **App won't launch**: Check permissions, try rebuilding
- **Conversion fails**: Verify input file integrity, check output permissions
- **Slow performance**: Close other applications, check available disk space
- **Audio sync issues**: Use different codec or adjust sample rate

### Error Codes
- **1001**: Input file not found or corrupted
- **1002**: Output location not writable
- **1003**: Unsupported format combination
- **1004**: Insufficient disk space
- **1005**: Conversion interrupted by user

### Getting Help
- **GitHub Issues**: Report bugs and feature requests
- **Documentation**: Comprehensive guides in `/docs` folder
- **Community**: Join discussions on GitHub Discussions

## Development

### Contributing
1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open Pull Request

### Code Style
- Swift 6 with strict concurrency
- SwiftUI best practices
- Comprehensive error handling
- Unit tests for core functionality

### Testing
```bash
# Run all tests
swift test

# Run specific test suite
swift test --filter ConversionEngineTests

# Test with real files
./scripts/test.sh
```

## License

MIT License - see LICENSE file for details.

## Changelog

### v2.4 (Current)
- ✅ Preset Manager with 15 built-in presets
- ✅ Custom preset creation and editing
- ✅ Real-time preset synchronization
- ✅ Dark mode support with semantic colors
- ✅ Improved window management
- ✅ Launch scripts for easy execution
- ✅ Comprehensive documentation

### v2.3
- Enhanced GUI with better layout
- Improved error handling
- Performance optimizations

### v2.2
- Video conversion support
- Batch processing capabilities
- Settings persistence

### v2.1
- Finder integration
- Menu bar controls
- Custom presets

### v2.0
- Complete SwiftUI rewrite
- Modern architecture
- Improved performance

### v1.0
- Initial release
- Basic audio conversion
- Simple GUI

## Credits

Developed by Andreas Sorby
Built with Swift 6, SwiftUI, and AVFoundation
App icon and branding by Andreas Sorby 