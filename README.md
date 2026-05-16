# EnglishAloud — AI Story Generator

> Generate custom English reading practice stories, powered by Cerebras AI.

**Live Demo:** [englishaloud.vercel.app](https://englishaloud.vercel.app) <!-- Replace with your actual URL -->

---

## What is it?

**EnglishAloud** is a web app that generates original English short stories tailored to your level and interests. It is designed for English learners who want engaging, level-appropriate reading material on demand — no account, no install required.

---

## Features

| Feature | Description |
|---|---|
| **AI-generated stories** | Fresh, original stories every time via Cerebras AI (Llama 3.1 8B) |
| **8 genres** | Adventure, Mystery, Sci-Fi, Fantasy, Slice of Life, Horror, Romance, Historical |
| **6 CEFR levels** | A1 through C2 — vocabulary and sentence complexity are adapted automatically |
| **3 story lengths** | Short (~200 words), Medium (~500 words), Long (~1000 words) |
| **Custom topic** | Optional keyword to steer the story (e.g. "the ocean", "a lost key") |
| **Read aloud** | Browser-native text-to-speech at a comfortable pace |
| **Word highlight** | Click any word to mark it while reading |
| **Copy & Print** | Copy the full story to clipboard or print a clean version |
| **Font size control** | Adjust reading size from the story toolbar |
| **Reading progress bar** | Tracks your scroll position through the story |
| **Fully responsive** | Works on desktop, tablet, and mobile |

---

## How to Use

### For readers (live site)

1. **Open the app** at the live demo link above.
2. **Pick a genre** from the tile grid on the left sidebar.
3. **Select your English level** using the CEFR chip buttons (A1 = Beginner → C2 = Proficiency).
4. **Choose a story length** — Short, Medium, or Long.
5. *(Optional)* **Enter a topic** in the text field to give the story a specific theme.
6. Press **Generate Story** and wait a few seconds.
7. Once the story appears, you can:
   - Press **🔊** to have the story read aloud.
   - Press **🖊️** to enter highlight mode, then click any word to mark it.
   - Press **📋** to copy the full story text.
   - Press **🖨️** to print a clean, ink-friendly version.
   - Drag the **text size slider** to adjust the font size.

---

## Project Structure

```
EnglishAloud/
├── index.html        # The entire frontend
├── api/
│   └── generate.js   # Vercel serverless function — proxies Cerebras API
└── README.md
```

The API key never touches the browser. The frontend calls `/api/generate`, the serverless function reads the key from Vercel's environment variables, and forwards the request to Cerebras.

---

## Deploying to Vercel

### 1. Push to GitHub

```bash
git add .
git commit -m "initial commit"
git push
```

### 2. Import the repo in Vercel

Go to [vercel.com/new](https://vercel.com/new), import your GitHub repository, and click **Deploy** (no build settings needed).

### 3. Add the environment variable

In your Vercel project, go to **Settings → Environment Variables** and add:

| Name | Value |
|---|---|
| `CEREBRAS_API_KEY` | your key from [cloud.cerebras.ai](https://cloud.cerebras.ai) |

### 4. Redeploy

After saving the variable, trigger a new deployment from the Vercel dashboard. The app will now be live with the key safely stored server-side.

---

## Running Locally

```bash
# Install the Vercel CLI (once)
npm i -g vercel

# Create a local .env file with your key
echo "CEREBRAS_API_KEY=your-key-here" > .env.local

# Start the local dev server (runs both the HTML and the serverless function)
vercel dev
```

> The `.env.local` file is already ignored by Vercel's default `.gitignore` rules. Never commit it.

---

## Tech Stack

- **Vanilla HTML / CSS / JavaScript** — zero dependencies, no framework
- **Cerebras AI API** — `llama3.1-8b` model for story generation
- **Vercel Serverless Functions** — Node.js API proxy to keep the key secret
- **Web Speech API** — browser-native text-to-speech
- **Google Fonts** — Playfair Display, Lora, Inter

---

## License

MIT — free to use, modify, and distribute.
