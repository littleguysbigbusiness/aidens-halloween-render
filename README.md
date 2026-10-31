# Aiden's Halloween Tracker — public dashboard

A tiny Flask app that holds live trick-or-treater tally stats in memory
(no database) and shows them on a public webpage. Paired with the local
tracker at https://github.com/littleguysbigbusiness/aidens-halloween-tracker,
which pushes stats here.

No camera footage or images ever pass through this service — just numbers
(count, last visit time, biggest group, etc).

## Deploy to Render

1. Push this repo to GitHub (done, if you're reading it there).
2. On Render (render.com), "New +" -> "Blueprint", point it at this repo.
3. Render reads render.yaml and deploys automatically, generating a
   TRACKER_SECRET environment variable for you.
4. Copy the deployed URL and the TRACKER_SECRET value (Dashboard -> your
   service -> Environment) into the local tracker's local_settings.py
   (or run `python setup.py` there) as RENDER_URL and RENDER_SECRET.

## Endpoints

- `GET /` - the public stats page (auto-refreshes every 5s).
- `POST /update` - the local tracker pushes stats here. Requires header
  `X-Tracker-Secret: <TRACKER_SECRET>`.
