# Review Insight Engine

**AI-powered product insight engine built with Gemini** - auto-detects key features, sentiment trends, and customer priorities from raw reviews.  
This Review Insight Engine turns noisy user feedback into structured summaries so you can instantly understand what matters most to your customers.

## Features

- Uses **Gemini AI** to analyze product reviews
- Automatically detects **key features** and their **positive/negative sentiments**
- Highlights what customers **love** (and hate)
- Accepts **CSV upload** of raw reviews
- Returns structured insights in JSON format
- Built with **React + TypeScript + Vite** for frontend and **Node.js (Vercel Function)** for backend

## Demo

Check out the live version here:  
[https://insight-gazer.vercel.app](https://insight-gazer.vercel.app)

## Project Structure

```
product-feature-gazer-72/
├── api/
│ └── analyze-reviews.ts # Vercel serverless backend (Gemini API call)
├── public/
├── src/
│ ├── components/ # UI components
│ ├── services/reviewService.ts # fetches analysis from backend
│ └── App.tsx
├── .env # (local only) API key for Gemini
├── package.json
└── tsconfig.json
```

## How It Works

1. User uploads a CSV file of product reviews.
2. The app sends a cleaned subset to the Gemini API.
3. Gemini responds with structured insight - category, features, sentiments, highlights.
4. Insight-Gazer displays it in an interactive UI.

## Environment Variables

In `.env` (not committed to GitHub), you must define:
GEMINI_API_KEY=your-gemini-api-key-here


On Vercel:
- Go to **Settings > Environment Variables** and set `GEMINI_API_KEY`

## Technologies Used

- **Frontend**: React + TypeScript + TailwindCSS + Vite
- **Backend**: Serverless Function via Vercel
- **AI**: Google Gemini (generative language model)

## Example Prompt Sent to Gemini

```json
{
  "productName": "Electric Toothbrush",
  "reviews": [
    { "review_text": "Really cleans well, battery lasts long!" },
    { "review_text": "Too loud. But otherwise effective." }
  ]
}
```

## Setup (For Local Development)

To test the backend locally, you'd need to replicate the serverless function using Express. In production, the backend is auto-deployed via Vercel.

### Clone repo
```bash
git clone https://github.com/DheetchanyaMohan/Insight-Gazer.git
cd Insight-Gazer
```

### Install dependencies
```
npm install
```

### Run dev server (frontend)
```
npm run dev
```

## Known Limitations
Gemini output may occasionally include malformed JSON (partially handled)

Rate-limited by Gemini API usage quota

Currently supports only English-language reviews
