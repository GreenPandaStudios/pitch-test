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
every push.

Pages has to be switched on once by a repository admin — the workflow token is
not allowed to create the site itself:

Settings → Pages → Build and deployment → Source → *GitHub Actions*

Then re-run the workflow (Actions → Deploy to GitHub Pages → Run workflow), or
just push again. The site lands at
`https://greenpandastudios.github.io/pitch-test/`.

Picking *Deploy from a branch* instead also works — point it at this branch
with the `/ (root)` folder — but then this workflow is redundant and will keep
failing, so delete it if you go that way.
