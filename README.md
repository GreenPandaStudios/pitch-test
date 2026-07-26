# One Shot — pitch match

A single-page ear-training game. It plays a random tone between G3 and C5, then
listens through the microphone while you sing or hum it back. You get one
attempt. The needle shows how far off you are in cents; octave is ignored, so
only the pitch class has to match.

Pitch detection is ACF2+ autocorrelation over the Web Audio API's time-domain
data — no dependencies, no build step, one file.

## Running it

Open `index.html` over `http://localhost` or any HTTPS origin. Microphone
access requires a secure context, so opening the file directly with `file://`
will not work.

```
python3 -m http.server 8000
# then visit http://localhost:8000
```

Headphones are recommended — speaker output leaking into the mic will be picked
up as your answer.

## Deploying

`.github/workflows/pages.yml` publishes the repository root to GitHub Pages on
every push. It needs Pages set to build from **GitHub Actions**:

Settings → Pages → Build and deployment → Source → *GitHub Actions*
