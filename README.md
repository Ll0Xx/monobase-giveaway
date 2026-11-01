# Monobase Giveaway

A single-page tool for running giveaways among Monobase subscribers from a CSV export.
Everything runs in the browser — the CSV never leaves your computer.

## Features

- Upload a Monobase CSV (UTF-8 or Windows-1251, `,` / `;` / tab delimited)
- Eligibility filters: active only, tiers, minimum amount, subscribed before a date, duplicates, manual exclude list
- Privacy mode (on by default): names, emails, IDs, phones and comments are masked; click any field to reveal just that one
- Randomness from [random.org](https://www.random.org) (keyless HTTP API, no sign-up) or local `crypto.getRandomValues`
- Draw animation, copy the winners list, export winners to CSV (masked or full)
- Ukrainian (default) and English UI

## Run locally

Open `index.html` in a browser. No build step, no dependencies.

## Publish on GitHub Pages

1. Create a new repository on GitHub and upload `index.html` (and optionally this README).
2. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then save.
3. After a minute the tool is available at `https://<your-username>.github.io/<repo-name>/`.

Don't commit subscriber exports to the repository — `*.csv` files are ignored by `.gitignore`.

## How the random.org draw works

The app requests a random permutation of `1..N` (N = number of eligible participants) from
`https://www.random.org/sequences/` and takes the first K entries as winners. Only N is sent —
no names or emails. The raw response is shown under the results. The quota is per visitor IP
(~1,000,000 bits/day), so sharing the tool doesn't use up anyone else's quota.
