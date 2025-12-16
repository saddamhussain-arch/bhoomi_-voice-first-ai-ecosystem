<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Run and deploy your AI Studio app

This contains everything you need to run your app locally.

View your app in AI Studio: https://ai.studio/apps/drive/1dsYl1rM_fjeBn-stAiEnN0hGdsf3Xwv9

## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Set the `GEMINI_API_KEY` in [.env.local](.env.local) to your Gemini API key
3. Run the app:
   `npm run dev`

## Deploy

- This project is configured to deploy to GitHub Pages using a GitHub Actions workflow.
- Ensure your repository's default branch is `main` (or update `.github/workflows/deploy.yml` to target your branch).
- The Vite `base` has been set to `./` so the build can be served from a subpath.

To manually test a production build locally:

```bash
npm ci
npm run build
npm run preview
```

When you push to `main`, the workflow will build and publish `dist/` to GitHub Pages.

## Deploy to Vercel

- Vercel can automatically build and deploy this project as a static site.
- This repo includes `vercel.json` configured to use the `dist` folder produced by `npm run build`.

Steps:

1. Import the repository into Vercel (https://vercel.com/new).
2. Set the **Build Command** to `npm run build` and **Output Directory** to `dist` (Vercel will detect these from `vercel.json`).
3. Add the environment variable `GEMINI_API_KEY` in the Vercel project settings (Environment Variables) so the app can access the Gemini key at build/runtime.
4. Deploy — Vercel will run the build and publish the site. For preview/development use Vercel's preview URLs.

Notes:

- `vite.config.ts` uses `base: './'` which works when serving from subpaths; Vercel serves at root so this is safe.
- If you want serverless functions or advanced routing, we can add a `vercel` folder with functions next.
