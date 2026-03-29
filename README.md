# 🧵 Wedesio Studio

**Wedesio Studio** is an AI-powered 3D t-shirt design tool. Generate custom SVG graphics using Google Gemini AI, place them on an interactive 3D shirt model, adjust colors and layouts, and export your design as a PNG — all in the browser.

---

## ✨ Features

- 🎨 **AI SVG Generation** — Describe a design in natural language; Gemini AI generates clean, scalable SVG artwork
- 🧥 **Interactive 3D Shirt** — Real-time 3D shirt preview powered by Three.js & React Three Fiber
- 🖌️ **Color Picker** — 16-color palette to instantly change the shirt color
- 📐 **Design Manager** — Layer-based system to position, scale, rotate, and adjust opacity of placed graphics
- 🔁 **Front / Back Toggle** — Switch between front and back shirt views
- 📤 **Export to PNG** — Capture your finished design as a high-quality PNG
- ⚡ **Fallback Mode** — Works with a mock SVG generator even without an API key

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, Vite 8 |
| 3D Rendering | Three.js, React Three Fiber, Drei |
| AI Backend | Google Gemini 2.5 Flash (`@google/genai`) |
| Server | Node.js, Express 5 |
| Styling | Vanilla CSS (Glassmorphism UI) |

---

## 📁 Project Structure

```
├── client/                  # React + Vite frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── AssetTools.jsx      # AI prompt + asset creation panel
│   │   │   ├── Viewport3D.jsx      # Three.js 3D shirt canvas
│   │   │   ├── ShirtModel.jsx      # 3D shirt mesh + decal renderer
│   │   │   └── DesignManager.jsx   # Layer controls for placed designs
│   │   ├── App.jsx
│   │   └── index.css
│   └── index.html
│
└── server/                  # Express backend
    ├── server.js            # API routes (Gemini SVG generation)
    ├── .env                 # Your API key (not committed)
    └── .env.example         # Template — copy this to .env
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or later
- A free [Google Gemini API key](https://aistudio.google.com/app/apikey)

---

### 1. Clone the repository

```bash
git clone https://github.com/your-username/wedesio-studio.git
cd wedesio-studio
```

### 2. Set up the server

```bash
cd server
npm install
cp .env.example .env
```

Open `server/.env` and fill in your key:

```env
GEMINI_API_KEY=your_gemini_api_key_here
PORT=5000
```

### 3. Set up the client

```bash
cd ../client
npm install
```

### 4. Run the app

Open **two terminals**:

**Terminal 1 — Backend:**
```bash
cd server
node server.js
# → Wedesio Studio Backend running on http://localhost:5000
```

**Terminal 2 — Frontend:**
```bash
cd client
npm run dev
# → http://localhost:5173
```

Then visit **[http://localhost:5173](http://localhost:5173)** in your browser.

---

## 🔑 Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GEMINI_API_KEY` | Yes | Your Google Gemini API key |
| `PORT` | No | Server port (default: `5000`) |

> Get a free API key at [Google AI Studio](https://aistudio.google.com/app/apikey)

---

## 📡 API Endpoints

| Method | Route | Description |
|--------|-------|-------------|
| `POST` | `/api/generate-svg` | Generate an SVG via Gemini AI |

**Request body:**
```json
{
  "prompt": "A roaring lion with tribal patterns",
  "style": "bold"
}
```

**Response:** Raw `image/svg+xml` content

---

## 🔒 Security

- The `.env` file is **gitignored** and will never be committed
- Always use `.env.example` as a reference template
- Never hardcode API keys in source files

---

## 📄 License

MIT © Wedesio Studio
