After reading the assignment instructions, I realized that I'm expected to build an app that enables real-time, bi-directional voice conversations between a human and an AI assistant.

To get started, I asked ChatGPT-5.1 for help using the following prompt:
```bash
I want to use LiveKit to enable real-time voice conversations between a human and an AI in the same room. When the user speaks through their microphone, the AI should immediately receive and process the audio, then respond with its own voice within the same LiveKit room.
```

Based on this prompt, ChatGPT suggested that I need to create the following project structure.
```
livekit-ai/
├── livekit-ai/         # Frontend
│   ├── app/page.tsx
│
├── livekit-token-server/       # Backend (token server)
│   ├── src/server.ts
│   ├── .env
│
├── livekit-voice-agent/        # LiveKit AI Agent worker
│   ├── agent.ts
│   ├── .env.local
```

First, I asked ChatGPT to build the token server using the following prompt:
```bash
Build a LiveKit Token Server using Node.js
```

After reading the token server code snippet, I realized that LiveKit environment variables were required, so I asked ChatGPT again
```bash
How can I generate LIVEKIT_API_KEY and LIVEKIT_API_SECRET?
```

After completing the token server, I asked ChatGPT to integrate the token API request into the frontend code using the following prompt:
```bash
Integrate the token api request into the frontend code. Make sure to provide me the complete code in page.tsx
```