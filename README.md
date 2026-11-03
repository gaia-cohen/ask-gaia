# Ask Gaia - portfolio site

Static page (`index.html`) plus one Netlify Function (`netlify/functions/chat.mjs`) that proxies the chat to the Gemini API.

## Environment variables (Netlify -> Site configuration -> Environment variables)
- `GEMINI_API_KEY` - required. From https://aistudio.google.com/apikey
- `GEMINI_MODEL` - optional. Defaults to `gemini-flash-lite-latest`. Pick a model your key can use (AI Studio -> Rate limits).
- `ALLOWED_ORIGIN` - optional, e.g. `https://gaia-cohen.netlify.app`. Blocks calls from other sites.

## How it behaves
- If the function is configured, the chat opens in Conversational mode (Gemini picks the tools; the tools, which run in the browser, own the facts).
- If the key is missing or the free quota is used up, it falls back to Instant mode automatically.

## Updating the content
Edit the `KB` object in `index.html`, then push to GitHub; Netlify redeploys automatically.
If you change tools, the prompt or tool descriptions, update `SYSTEM` and `TOOLS` in `chat.mjs` too.
