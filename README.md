# Chat Input with Speech-to-Text

A sleek, modern chat input component with voice input support — type your message or tap the microphone and speak. Built with Next.js, shadcn/ui, and the Web Speech API.

![Next.js](https://img.shields.io/badge/Next.js-15-black?logo=next.js)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38B2AC?logo=tailwindcss)

## What it does

This project provides a polished chat-message input UI — the kind you'd see in modern AI chat apps. It pairs a multiline text area with a **speech-to-text microphone button** powered by the browser's Web Speech API, so users can dictate messages instead of typing them. Messages render as chat bubbles with a clean, responsive layout, complete with dark/light theme support.

## Features

- 🎙️ **Speech-to-text voice input** — press-and-talk dictation via the Web Speech API (`SpeechRecognition`)
- 💬 **Chat message display** — messages rendered as styled bubbles in a scrollable thread
- ✍️ **Multiline input** — auto-growing textarea with send button and keyboard shortcuts
- 🌓 **Dark / light mode** — theme toggle powered by `next-themes`
- 🧩 **shadcn/ui components** — accessible Radix-based primitives (buttons, tooltips, avatars, scroll areas)
- 📱 **Responsive design** — works on mobile and desktop
- ⚡ **Static site** — exports to fully static HTML, deployable anywhere

## Tech stack

| Layer       | Tech                                             |
|-------------|--------------------------------------------------|
| Framework   | Next.js 15 (App Router, static export)           |
| UI library  | React 19                                         |
| Language    | TypeScript 5                                     |
| Styling     | Tailwind CSS 3 + `tailwindcss-animate`           |
| Components  | shadcn/ui (Radix UI primitives)                  |
| Icons       | Lucide React                                     |
| Voice input | Web Speech API (browser-native, no server needed) |

## Quick start

**Prerequisites:** Node.js 18+ and npm.

```bash
# Install dependencies
npm install

# Run the dev server
npm run dev
# Open http://localhost:3000
```

**Build a static site:**

```bash
npm run build
# Static output is generated in ./out — serve it with any static host
npx serve out
```

> Note: speech recognition requires a browser with Web Speech API support (e.g. Chrome/Edge) and microphone permission.

## Project structure

```
.
├── app/
│   ├── layout.tsx        # Root layout, theme provider, global styles
│   ├── page.tsx          # Chat page — message list + input
│   └── globals.css       # Tailwind + theme CSS variables
├── components/
│   ├── chat-input.tsx    # Chat input with mic (speech-to-text) button
│   ├── theme-provider.tsx
│   └── ui/               # shadcn/ui primitives (button, avatar, tooltip, ...)
├── lib/
│   └── utils.ts          # cn() class merge helper
├── public/               # Static assets
├── next.config.mjs       # Static export config (output: 'export')
└── tailwind.config.ts
```

## Environment variables

None required — everything runs client-side. The Web Speech API is browser-native.

## Deployment

The app is configured with `output: 'export'`, so `npm run build` produces a static site in `out/` that can be deployed to any static host:

- **Cloudflare Pages:** `cloudflare pages_deploy chat-input-with-speech-to-te out/`
- **Vercel / Netlify / GitHub Pages:** point at the `out/` directory after `npm run build`

## How speech-to-text works

The microphone button uses `window.SpeechRecognition` (or `webkitSpeechRecognition`). When recording starts, interim transcripts stream into the input field in real time; stopping the recorder finalizes the text so it can be edited or sent like a typed message. Browsers without the API simply hide/disable the mic button.

## License

MIT — free to use and modify.

---

Built by Girish Lade · [ladestack.in](https://ladestack.in)
