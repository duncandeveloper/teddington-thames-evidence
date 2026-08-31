# Ground rules — River Thames Evidence Programme

This is a **public evidence site that regulators read**. The Environment Agency has the
link. Credibility is the product; one unsourced or overstated figure costs more than a
missing page.

The full operating layer — charter, ways of working, work-threads, agent prompts, decision
log, correspondence register — lives in the private companion repository
`duncandeveloper/thames-evidence-programme`. Clone it alongside this one and start at its
`ops/README.md`. What follows is the short version that governs *this* repo.

## The eight non-negotiables

1. **Every figure carries a citation and a provenance tag**: `RAW-PULL` · `PUBLISHED` ·
   `DERIVED` · `ACCESS-BLOCKED`.
2. **Never invent a number.** If it is not in the datastore or FINDINGS, write `TODO` and
   say what would settle it. An honest gap is evidence in this programme; a plausible
   fabrication is fatal to it.
3. **Always show the fairness caveats.** Worst dissolved-oxygen is historical (2004–06) and
   recent years improved; EDM spill hours are rainfall-driven and volatile, not a trend;
   the chemical "Fail" is largely a national artefact; tidal biology is healthy; NBN trends
   reflect recording effort, not population; correlation is not causation.
4. **Legal precision on people and companies.** Charged is not convicted. A regulatory
   penalty is not a criminal conviction. Proposed is not levied. Never label an individual
   a criminal on charges alone. Presumption of innocence, every time.
5. **No JavaScript on static pages.** The global CSP is `script-src 'none'` and charts are
   inline SVG. A page that needs JS gets a *scoped* relaxation in
   `staticwebapp.config.json` for that route only — see `/docs/correlations.html`.
6. **The two zones stay visually distinct.** Neutral Evidence pages never inherit the
   bolder Awareness styling. That separation is what protects credibility with the EA.
7. **This repository is public.** FOI/EIR correspondence never enters it. Before
   committing, check for personal contact details of private individuals. Official role
   mailboxes and published representatives are fine; named volunteers and personal
   addresses are not.
8. **Corrections are published, not buried.** If a figure is wrong, fix it, say that it was
   fixed, and credit whoever caught it.

## Geography — get this right

The reach spans **two** water bodies, split at Teddington Weir, the tidal limit:

- **Above** the weir (Kingston, Ham, including the bathing site): `GB106039023232`
  Thames (Egham to Teddington), freshwater, ecological **Poor**.
- **Below** the weir (Richmond, Isleworth, the Mogden outfall): `GB530603911403`
  **THAMES UPPER**, transitional, ecological **Moderate**, with
  `Hydrological Regime: Does Not Support Good` (2022).

`GB530603911402` (THAMES MIDDLE) runs Battersea to the outer estuary and **does not touch
this reach**. Earlier pages used it in error.

## Line endings and pushes

`.gitattributes` normalises everything to LF. If `git status` shows dozens of whole-file
diffs, run `git add --renormalize .` — do not commit the churn.

**Every push to `main` redeploys the live site in about 90 seconds. Treat a push as a
publish.**
