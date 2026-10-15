# Orbit: Space Quiz

Orbit is a small, space-themed quiz that tests your astronomy knowledge with 10 questions. It includes animated answer feedback, a score and progress indicator, and a results screen with a shareable score.

## Run locally

No build step or dependencies are required. From the project directory, start Python's built-in web server:

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000) in your browser. You can also open `index.html` directly.

## Deployment

The site is deployed to GitHub Pages from the `main` branch using the workflow in `.github/workflows/deploy-pages.yml`. Pull requests run a lightweight check to confirm the static entry point and this README are present.
