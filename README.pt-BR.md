# 🎙️ Audio Orb - IA de Voz Open Source

<div align="center">

![Banner do Audio Orb](https://img.shields.io/badge/Audio-Orb-blue?style=for-the-badge&logo=audio&logoColor=white)
[![Licença MIT](https://img.shields.io/badge/Licen%C3%A7a-MIT-green.svg?style=for-the-badge)](LICENSE)
[![Open Source](https://img.shields.io/badge/Open-Source-orange?style=for-the-badge)](https://opensource.org)

**IA de voz em tempo real com motores TTS open source e visualização 3D de áudio impressionante**

[Recursos](#-recursos) • [Demo](#-demo) • [Instalação](#-instalação) • [Uso](#-uso) • [Contribuindo](#-contribuindo)

---

[🇺🇸 English](README.md) | **🇧🇷 Português (Brasil)**

</div>

---

## 📋 Visão Geral

**Audio Orb** é uma aplicação avançada de IA de voz que combina:
- 🎤 **Processamento de áudio em tempo real** com Gemini Live API
- 🔊 **Múltiplos motores TTS**: Google Gemini, Coqui XTTS, Piper TTS
- 🌍 **Suporte multilíngue**: mais de 17 idiomas
- 🎨 **Visualização 3D de áudio**: Orbe interativo com efeitos WebGL
- 🎭 **Clonagem de voz**: Clone qualquer voz com apenas 6-10 segundos de áudio
- 🚀 **100% baseado em navegador** - opções disponíveis

## ✨ Recursos

### Motores de Síntese de Voz

#### 🔹 Vozes Gemini (Padrão)
- **Puck** (padrão)
- Charon, Kore, Fenrir, Aoede, Zephyr
- Baseado em nuvem, alta qualidade
- Baixa latência

#### 🔹 Coqui XTTS-v2
- ⭐ **Clonagem de voz** a partir de amostras de 6 segundos
- 🌐 17 idiomas suportados
- 🎭 Transferência emocional e de estilo
- 📡 Implantação auto-hospedada ou em nuvem

#### 🔹 Piper TTS
- 🚀 **Mais de 900 vozes neurais**
- 💻 100% local, baseado em navegador
- ⚡ Ultra-rápido (10x tempo real)
- 🔒 Focado em privacidade, sem nuvem

### Recursos Técnicos

- 🎨 **Visualização 3D**
  - Esfera com WebGL e reatividade ao áudio
  - Mapeamento de ambiente HDR
  - Análise de espectro em tempo real
  
- 🔧 **Arquitetura Modular**
  - Fácil adição de novos motores TTS
  - Sistema de plugins para provedores de voz
  - TypeScript + componentes Lit

- 🌐 **Padrões Web**
  - WebRTC para áudio
  - Web Audio API
  - MediaRecorder API

## 🚀 Início Rápido

### Pré-requisitos

```bash
Node.js >= 18.0
npm ou yarn
Chave de API do Google AI Studio (para Gemini)
```

### Instalação

```bash
# Clone o repositório
git clone https://github.com/AD-Thiago/audio-orb-opensource.git
cd audio-orb-opensource

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env e adicione suas chaves de API

# Execute o servidor de desenvolvimento
npm run dev
```

### Variáveis de Ambiente

```env
# API Gemini (obrigatório para configuração padrão)
GEMINI_API_KEY=sua_chave_api_aqui

# Opcional: Servidor XTTS
XTTS_API_URL=http://localhost:5002

# Opcional: Servidor Piper  
PIPER_API_URL=http://localhost:8080
```

## 🎮 Uso

### Chat de Voz Básico

1. Abra a aplicação
2. Selecione uma voz no menu suspenso
3. Clique no botão do microfone
4. Comece a falar
5. A IA responde com voz sintetizada

### Adicionando Vozes Personalizadas (XTTS)

```typescript
// 1. Grave ou prepare 6-10 segundos de áudio de voz
// 2. Coloque no diretório /voices
// 3. Adicione à configuração

const customVoices = [
  {
    name: 'Minha Voz',
    file: './voices/minha_voz.wav',
    engine: 'xtts'
  }
];
```

### Usando Piper (100% Local)

```bash
# Opção 1: Docker
docker run -p 8080:8080 gcr.io/clowerweb/tts-studio

# Opção 2: Use a demo online
# Visite: https://clowerweb.github.io/tts-studio
# Baixe vozes e integre
```

## 🏗️ Arquitetura

```
audio-orb-opensource/
├── src/
│   ├── index.tsx          # Componente principal da aplicação
│   ├── visual-3d.ts       # Visualização 3D
│   ├── analyser.ts        # Análise de áudio
│   ├── engines/
│   │   ├── gemini.ts      # Integração Gemini
│   │   ├── xtts.ts        # Integração XTTS
│   │   └── piper.ts       # Integração Piper
│   └── utils.ts
├── public/
│   └── voices/            # Amostras de voz
├── docs/                  # Documentação
└── README.md
```

## 🔧 Configuração

### Adicionando Novos Motores TTS

A aplicação suporta motores TTS plugáveis:

```typescript
interface TTSEngine {
  name: string;
  synthesize(text: string, voice: string): Promise<AudioBuffer>;
  listVoices(): Promise<Voice[]>;
}

// Implemente e registre
registerEngine(new MeuMotorTTSPersonalizado());
```

## 📊 Performance

| Motor | Latência | Qualidade | Idiomas | Local |
|-------|----------|-----------|---------|-------|
| Gemini | ~200ms | ⭐⭐⭐⭐⭐ | 40+ | ❌ |
| XTTS | ~300ms | ⭐⭐⭐⭐⭐ | 17 | ✅ |
| Piper | ~50ms | ⭐⭐⭐⭐ | 50+ | ✅ |

## 🤝 Contribuindo

Contribuições são bem-vindas! Por favor, consulte [CONTRIBUTING.pt-BR.md](CONTRIBUTING.pt-BR.md) para diretrizes.

### Áreas para Contribuir

- 🎤 Adicionar novas integrações de motores TTS
- 🎨 Melhorar visualizações 3D
- 🌍 Adicionar suporte a idiomas
- 🐛 Correções de bugs e melhorias
- 📚 Documentação

### Configuração para Desenvolvimento

```bash
# Faça fork e clone
git clone https://github.com/SEU_USUARIO/audio-orb-opensource.git

# Crie uma branch de feature
git checkout -b feature/funcionalidade-incrivel

# Faça alterações e teste
npm run dev
npm test

# Commit e push
git commit -m 'Adicionar funcionalidade incrível'
git push origin feature/funcionalidade-incrivel

# Abra um Pull Request
```

## 📜 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 🙏 Agradecimentos

- **Google Gemini** - Pela Gemini Live API
- **Coqui AI** - Pelo incrível modelo XTTS
- **Projeto Piper** - Pelas vozes open source de alta qualidade
- **Comunidade WebGL** - Pelos recursos de renderização 3D

## 📖 Recursos

- [Documentação Coqui TTS](https://github.com/coqui-ai/TTS)
- [Vozes Piper TTS](https://github.com/rhasspy/piper)
- [Google AI Studio](https://aistudio.google.com)
- [Fundamentos WebGL](https://webglfundamentals.org)

## 🔗 Links

- 🌐 [Demo ao Vivo](https://audio-orb-demo.vercel.app) _(em breve)_
- 📝 [Post no Blog](https://blog.example.com/audio-orb) _(em breve)_
- 💬 [Comunidade Discord](https://discord.gg/audio-orb) _(em breve)_

## 📞 Contato

Para dúvidas ou suporte, por favor [abra uma issue](https://github.com/AD-Thiago/audio-orb-opensource/issues).

---

<div align="center">

**⭐ Dê uma estrela neste repositório se você achar útil!**

Feito com ❤️ pela comunidade Audio Orb

</div>
