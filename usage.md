# Simple Media Encoder - Usage Guide

## Overview
Simple Media Encoder is a macOS application for converting video and audio files with professional-grade presets and customization options.

## Basic Usage

### 1. Adding Files
- **Drag & Drop**: Drop files directly onto the purple drop zone
- **Browse Button**: Click "Browse..." to select files using Finder
- **Multiple Files**: Add multiple files for batch conversion

### 2. Selecting Presets
The app includes 15 professional presets organized by category:

**Professional Video Presets:**
- ProRes 4K Master - Archival quality MOV with 4K resolution
- H.264 High 4K - High-quality 4K with PCM audio
- H.265 Master - 4K H.265 with PCM audio
- ProRes 1080p LT - Professional 1080p with PCM audio

**Consumer Video Presets:**
- YouTube 4K - Optimized for YouTube 4K uploads
- YouTube 1080p - Optimized for YouTube 1080p uploads
- Mobile HD - Compressed 720p for mobile devices
- Archival 4K - Long-term storage with H.265 and ALAC

**Professional Audio Presets:**
- WAV 24/48 (PCM) - Uncompressed 24-bit/48kHz
- WAV 24/96 (PCM) - Uncompressed 24-bit/96kHz
- AIFF 16/44.1 (PCM) - Standard CD quality
- ALAC 24/96 - Lossless compressed audio

**Consumer Audio Presets:**
- AAC 256k/44.1 - High-quality compressed audio
- AAC 128k/44.1 - Standard compressed audio
- M4A 192k/48 - Balanced quality and size

### 3. Converting Files
1. Select your files
2. Choose a preset or customize settings
3. Click the "Convert" button
4. Monitor progress in the bottom bar

## Advanced Features

### Preset Manager
Access the Preset Manager through **Menu → Preset Manager** or **Cmd+Shift+P**.

The Preset Manager provides:
- **Full Preset Editing**: Modify all settings for any preset
- **Custom Presets**: Create new presets based on existing ones
- **Preset Management**: Add, duplicate, rename, and delete presets
- **Factory Reset**: Restore original presets with one click

**Preset Manager Features:**
- **Compact List View**: Icon-based list showing video/audio presets with format indicators
- **Real-time Editing**: Edit preset names, codecs, quality settings, and audio parameters
- **Save Changes**: Apply modifications with the Save button
- **Duplication**: Create copies of presets for customization
- **Deletion**: Remove custom presets (default presets are restored on factory reset)

**Editing Capabilities:**
- Preset names (fully editable)
- Output formats (MP4, MOV, AIFF, WAV, M4A)
- Video codecs (H.264, H.265)
- Video resolution (720p, 1080p, 4K)
- Quality settings (CRF values)
- Audio codecs (AAC, ALAC, PCM)
- Audio bitrates (128k, 192k, 256k, 320k)
- Sample rates (44.1kHz, 48kHz, 96kHz)
- Bit depths (16-bit, 24-bit)

### Settings Panel
Access settings through **Menu → Settings** or **Cmd+,**.

Configure:
- **Dark Mode**: Toggle between light and dark themes
- **File Naming**: Include conversion settings in filenames
- **Output Directory**: Choose where converted files are saved
- **Overwrite Behavior**: Handle existing files
- **Subfolder Creation**: Organize output by format

### Finder Integration
- **Right-click Integration**: Convert files directly from Finder context menu
- **Quick Actions**: Access conversion through macOS Quick Actions
- **Drag & Drop**: Seamless file handling from Finder

## File Format Support

### Input Formats
- **Video**: MP4, MOV, AVI, MKV, and most common formats
- **Audio**: MP3, WAV, AIFF, M4A, FLAC, and most common formats

### Output Formats
- **Video**: MP4 (H.264/H.265), MOV (H.264/H.265)
- **Audio**: WAV (PCM), AIFF (PCM), M4A (AAC/ALAC)

## Keyboard Shortcuts
- **Cmd+,**: Open Settings
- **Cmd+Shift+P**: Open Preset Manager
- **Cmd+O**: Browse for files
- **Cmd+R**: Start conversion
- **Cmd+Q**: Quit application

## Tips for Best Results
1. **Use appropriate presets**: Choose video presets for video files, audio presets for audio files
2. **Batch processing**: Add multiple files for efficient batch conversion
3. **Quality vs. Size**: Higher CRF values = smaller files but lower quality
4. **Audio quality**: Use PCM for archival, AAC for distribution
5. **Custom presets**: Create presets for your specific workflow needs

## Troubleshooting
- **Conversion fails**: Check input file format compatibility
- **Slow conversion**: Lower quality settings or resolution for faster processing
- **Large output files**: Increase CRF value or use compressed audio codecs
- **Audio issues**: Ensure audio codec matches your intended use case

## Version History
- **v2.4**: Added Preset Manager with full editing capabilities
- **v2.3**: Enhanced UI with dark mode support
- **v2.2**: Added Finder integration and Quick Actions
- **v2.1**: Improved conversion engine reliability
- **v2.0**: Complete rewrite with modern SwiftUI interface 