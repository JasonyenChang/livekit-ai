# Real-Time AI Voice Conversation Starter

A simple full-stack application demonstrating real-time bi-directional voice conversation between a human and an AI assistant using [LiveKit Javascript SDK](https://github.com/livekit/client-sdk-js), [Next.js](https://nextjs.org/docs/app/getting-started/installation), and an [AI Voice Agent](https://docs.livekit.io/agents/start/voice-ai/#starters).

This application implements:

- Real-time audio streaming
- Human → AI → Human voice loop
- LiveKit token server
- Frontend React UI + audio playback
- AI agent with LLM, STT, TTS

### Features:

Frontend (Next.js + React + TypeScript)

- Clean UI
- Start Conversation / End Conversation
- Connection status indicator
- Microphone on/off indicator
- Subscribes to AI audio tracks from LiveKit room
- Plays AI-generated audio in real time

Backend (Node.js + Express)

- Issues LiveKit Access Tokens
- Provides room URL, room name, identity

AI Agent (LiveKit Agents SDK)

- Listens for user speech
- VAD (voice activity detection)
- STT (AssemblyAI universal streaming)
- LLM (OpenAI GPT-4.1-mini)
- TTS (Cartesia Sonic 3)
- Sends audio back to room as LiveKit track

### Project structure

```
agent-starter-react/
├── app/
│   ├── (app)/
│   ├── api/
│   ├── components/
│   ├── fonts/
│   ├── globals.css
│   └── layout.tsx
├── components/
│   ├── livekit/
│   ├── ui/
│   ├── app.tsx
│   ├── session-view.tsx
│   └── welcome.tsx
├── hooks/
├── lib/
├── public/
└── package.json
```

## Getting started

> [!TIP]
> If you'd like to try this application without modification, you can deploy an instance in just a few clicks with [LiveKit Cloud Sandbox](https://cloud.livekit.io/projects/p_/sandbox/templates/agent-starter-react).

[![Open on LiveKit](https://img.shields.io/badge/Open%20on%20LiveKit%20Cloud-002CF2?style=for-the-badge&logo=external-link)](https://cloud.livekit.io/projects/p_/sandbox/templates/agent-starter-react)

Run the following command to automatically clone this template.

```bash
lk app create --template agent-starter-react
```

Then run the app with:

```bash
pnpm install
pnpm dev
```

And open http://localhost:3000 in your browser.

You'll also need an agent to speak with. Try our starter agent for [Python](https://github.com/livekit-examples/agent-starter-python), [Node.js](https://github.com/livekit-examples/agent-starter-node), or [create your own from scratch](https://docs.livekit.io/agents/start/voice-ai/).

## Configuration

This starter is designed to be flexible so you can adapt it to your specific agent use case. You can easily configure it to work with different types of inputs and outputs:

#### Example: App configuration (`app-config.ts`)

```ts
export const APP_CONFIG_DEFAULTS: AppConfig = {
  companyName: 'LiveKit',
  pageTitle: 'LiveKit Voice Agent',
  pageDescription: 'A voice agent built with LiveKit',

  supportsChatInput: true,
  supportsVideoInput: true,
  supportsScreenShare: true,
  isPreConnectBufferEnabled: true,

  logo: '/lk-logo.svg',
  accent: '#002cf2',
  logoDark: '/lk-logo-dark.svg',
  accentDark: '#1fd5f9',
  startButtonText: 'Start call',

  // for LiveKit Cloud Sandbox
  sandboxId: undefined,
  agentName: undefined,
};
```

You can update these values in [`app-config.ts`](./app-config.ts) to customize branding, features, and UI text for your deployment.

> [!NOTE]
> The `sandboxId` and `agentName` are for the LiveKit Cloud Sandbox environment.
> They are not used for local development.

#### Environment Variables

You'll also need to configure your LiveKit credentials in `.env.local` (copy `.env.example` if you don't have one):

```env
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
LIVEKIT_URL=https://your-livekit-server-url
```

These are required for the voice agent functionality to work with your LiveKit project.

## Contributing

This template is open source and we welcome contributions! Please open a PR or issue through GitHub, and don't forget to join us in the [LiveKit Community Slack](https://livekit.io/join-slack)!