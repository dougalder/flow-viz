# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-10-24

### Added

- **33 Visual Styles**: Complete collection of music-reactive visual effects
  - Particles, Ribbons, Geometric, Organic, Synaptic, Space, and Abstract categories
  - Each style has randomized variations for long tracks
  - Full spectrum response with beat detection

- **Audio Input Options**:
  - File upload (WAV, MP3, OGG, FLAC, etc.)
  - Microphone input for live visualization
  - Seek timeline for precise positioning

- **Visual Customization**:
  - Amplitude sensitivity (0.0–2.0)
  - Motion speed (0.2–2.0)
  - Trail persistence (0.0–1.0)
  - Particle density (0.0–2.0)
  - Pattern complexity (0.0–2.0)
  - Color saturation (0.0–1.0)
  - Hue rotation (-180–180°)

- **Mood & Color System**:
  - Theme-aware colors (dark/light mode)
  - Beat-driven color pulses
  - Hue shifting across style transitions
  - Automatic color variation per style load

- **Video Export**:
  - Multiple resolutions: 720p, 1080p, 1440p, 2160p (4K)
  - Multiple frame rates: 24, 30, 60 fps
  - Format options: MP4 (H.264), WebM (VP9)
  - Audio included in exports
  - Custom or full-track duration

- **Auto-Flow Mode**:
  - Automatic style cycling on timer or beat
  - Customizable transition duration
  - Beat-sync toggle

- **Theme Toggle**:
  - Dark and light modes
  - Fully responsive design
  - Mobile & tablet support
  - iOS/Safari compatible

- **Performance**:
  - Low-resolution internal rendering with upscaling
  - Real-time FFT analysis (512-sample frames)
  - Target 60 fps on modern hardware
  - Optimized for desktop and mobile

- **Interface**:
  - Tabbed control layout (Styles, Visuals, Export)
  - Real-time audio meters (bass, mids, treble)
  - FPS counter and HUD
  - Status indicators (Idle, Paused, Playing, Recording)

- **Documentation**:
  - Comprehensive README with feature overview
  - Detailed user manual with screenshots
  - API documentation for style creation
  - Contributing guidelines

- **Keyboard Shortcuts**:
  - Space: Play/Pause
  - T: Toggle theme
  - A: Toggle auto-flow
  - M: Microphone input
  - R: Record/stop
  - Arrow keys: Seek

### Technical Details

- **No Dependencies**: Self-contained single HTML file
- **Browser APIs Used**:
  - Web Audio API (audio input, analysis, playback)
  - Canvas 2D (rendering)
  - MediaRecorder API (video export)
- **Compatibility**: Chrome 90+, Firefox 88+, Safari 15+, Edge 90+

### Known Limitations

- MediaRecorder API not available in IE 11 or older browsers
- Some older Android devices may experience performance issues
- Microphone input requires HTTPS on most browsers (except localhost)
- Browser autoplay policies may require user interaction

---

## Future Versions

### Planned for 1.1.0
- WebGL rendering pipeline for advanced effects
- Adjustable color palettes and theme editor
- Preset save/load system
- More visual styles (targeting 50+)

### Planned for 1.2.0
- MIDI/OSC input support
- Collaborative streaming mode
- VR/immersive mode support
- Plugin system for custom styles

### Planned for 2.0.0
- Real-time spectrum analyzer view
- Beat-by-beat timeline editor
- Multi-track audio blending
- AI-powered automatic style selection

---

## Version History

### [1.0.0] - October 24, 2026
Initial public release with 33 visual styles, full audio analysis, video export, and comprehensive documentation.

---

## How to Report Issues

Found a bug or have a suggestion? Please open an issue with:
- Browser and OS version
- Steps to reproduce
- Screenshots/video if applicable
- Expected vs. actual behavior

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.
