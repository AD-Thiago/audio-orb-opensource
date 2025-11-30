# 🎙️ Audio Orb - Open Source Voice AI

<div align="center">

![Audio Orb Banner](https://img.shields.io/badge/Audio-Orb-blue?style=for-the-badge&logo=audio&logoColor=white)
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![Open Source](https://img.shields.io/badge/Open-Source-orange?style=for-the-badge)](https://opensource.org)

**Real-time voice AI with open source TTS engines and stunning 3D audio visualization**

[Features](#-features) • [Demo](#-demo) • [Installation](#-installation) • [Usage](#-usage) • [Contributing](#-contributing)

</div>

---

## 📋 Overview

**Audio Orb** is an advanced voice AI application that combines:
- 🎤 **Real-time audio processing** with Gemini Live API
- 🔊 **Multiple TTS engines**: Google Gemini, Coqui XTTS, Piper TTS
- 🌍 **Multilingual support**: 17+ languages
- 🎨 **3D audio visualization**: Interactive orb with WebGL effects
- 🎭 **Voice cloning**: Clone any voice with just 6-10 seconds of audio
- 🚀 **100% browser-based** options available

## ✨ Features

### Voice Synthesis Engines

#### 🔹 Gemini Voices (Default)
- **Puck** (default)
- Charon, Kore, Fenrir, Aoede, Zephyr
- Cloud-based, high quality
- Low latency

#### 🔹 Coqui XTTS-v2
- ⭐ **Voice cloning** from 6-second samples
- 🌐 17 languages supported
- 🎭 Emotional and style transfer
- 📡 Self-hosted or cloud deployment

#### 🔹 Piper TTS
- 🚀 **900+ neural voices**
- 💻 100% local, browser-based
- ⚡ Ultra-fast (10x realtime)
- 🔒 Privacy-first, no cloud

### Technical Features

- 🎨 **3D Visualization**
  - WebGL-powered sphere with audio reactivity
  - HDR environment mapping
  - Real-time spectrum analysis
  
- 🔧 **Modular Architecture**
  - Easy to add new TTS engines
  - Plugin system for voice providers
  - TypeScript + Lit components

- 🌐 **Web Standards**
  - WebRTC for audio
  - Web Audio API
  - MediaRecorder API

## 🚀 Quick Start

### Prerequisites

```bash
Node.js >= 18.0
npm or yarn
Google AI Studio API Key (for Gemini)
```

### Installation

```bash
# Clone the repository
git clone https://github.com/AD-Thiago/audio-orb-opensource.git
cd audio-orb-opensource

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env and add your API keys

# Run development server
npm run dev
```

### Environment Variables

```env
# Gemini API (required for default setup)
GEMINI_API_KEY=your_api_key_here

# Optional: XTTS Server
XTTS_API_URL=http://localhost:5002

# Optional: Piper Server  
PIPER_API_URL=http://localhost:8080
```

## 🎮 Usage

### Basic Voice Chat

1. Open the application
2. Select a voice from the dropdown
3. Click the microphone button
4. Start speaking
5. The AI responds with synthesized voice

### Adding Custom Voices (XTTS)

```typescript
// 1. Record or prepare 6-10 seconds of voice audio
// 2. Place in /voices directory
// 3. Add to configuration

const customVoices = [
  {
    name: 'My Voice',
    file: './voices/my_voice.wav',
    engine: 'xtts'
  }
];
```

### Using Piper (100% Local)

```bash
# Option 1: Docker
docker run -p 8080:8080 gcr.io/clowerweb/tts-studio

# Option 2: Use online demo
# Visit: https://clowerweb.github.io/tts-studio
# Download voices and integrate
```

## 🏗️ Architecture

```
audio-orb-opensource/
├── src/
│   ├── index.tsx          # Main app component
│   ├── visual-3d.ts       # 3D visualization
│   ├── analyser.ts        # Audio analysis
│   ├── engines/
│   │   ├── gemini.ts      # Gemini integration
│   │   ├── xtts.ts        # XTTS integration
│   │   └── piper.ts       # Piper integration
│   └── utils.ts
├── public/
│   └── voices/            # Voice samples
├── docs/                  # Documentation
└── README.md
```

## 🔧 Configuration

### Adding New TTS Engines

The app supports pluggable TTS engines:

```typescript
interface TTSEngine {
  name: string;
  synthesize(text: string, voice: string): Promise<AudioBuffer>;
  listVoices(): Promise<Voice[]>;
}

// Implement and register
registerEngine(new MyCustomTTSEngine());
```

## 📊 Performance

| Engine | Latency | Quality | Languages | Local |
|--------|---------|---------|-----------|-------|
| Gemini | ~200ms | ⭐⭐⭐⭐⭐ | 40+ | ❌ |
| XTTS | ~300ms | ⭐⭐⭐⭐⭐ | 17 | ✅ |
| Piper | ~50ms | ⭐⭐⭐⭐ | 50+ | ✅ |

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Areas to Contribute

- 🎤 Add new TTS engine integrations
- 🎨 Improve 3D visualizations
- 🌍 Add language support
- 🐛 Bug fixes and improvements
- 📚 Documentation

### Development Setup

```bash
# Fork and clone
git clone https://github.com/YOUR_USERNAME/audio-orb-opensource.git

# Create feature branch
git checkout -b feature/amazing-feature

# Make changes and test
npm run dev
npm test

# Commit and push
git commit -m 'Add amazing feature'
git push origin feature/amazing-feature

# Open Pull Request
```

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Google Gemini** - For the Gemini Live API
- **Coqui AI** - For the amazing XTTS model
- **Piper Project** - For high-quality open source voices
- **WebGL Community** - For 3D rendering resources

## 📖 Resources

- [Coqui TTS Documentation](https://github.com/coqui-ai/TTS)
- [Piper TTS Voices](https://github.com/rhasspy/piper)
- [Google AI Studio](https://aistudio.google.com)
- [WebGL Fundamentals](https://webglfundamentals.org)

## 🔗 Links

- 🌐 [Live Demo](https://audio-orb-demo.vercel.app) _(coming soon)_
- 📝 [Blog Post](https://blog.example.com/audio-orb) _(coming soon)_
- 💬 [Discord Community](https://discord.gg/audio-orb) _(coming soon)_

## 📞 Contact

For questions or support, please [open an issue](https://github.com/AD-Thiago/audio-orb-opensource/issues).

---

<div align="center">

**⭐ Star this repository if you find it useful!**

Made with ❤️ by the Audio Orb community

</div>
