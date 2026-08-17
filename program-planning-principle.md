# Program-planning principle — modelling the most complex transaction

Companion note to `after-sales-channel-partner-brief.md` and `BRIEF.md`. Captures
the operating principle that justifies building the data model from warranty &
after-sales down, rather than from retail-sale up.

---

## The principle in one line

**Model the most complex transaction first. Every other volume is a subset of
that model.**

## Why this is now practical

Advanced AI-assisted data processing changes the economics of the classical
"top-down data model" approach in two ways:

1. **Guess-then-test replaces analyse-then-guess.**
   AI can propose the most complex transaction shape *from the data lake as it
   sits today* and then test the guess against real record populations. This
   collapses months of workshops into a working hypothesis in days.
2. **"More than perfect" is the standard for program planning.**
   For decisions where each **million dollars spent is graded against a hard
   business return**, a directionally right, dynamically updating model beats
   a perfectionist static model that is stale on delivery.

Once one of these models is stood up:

- It **updates dynamically** as deployments land.
- When a deployment does **not return what was expected**, the gap between
  modelled prediction and actual result tells you **where to look** and
  **how to improve** the next release.
- Every deployment becomes an input signal into the model, not just a cost.

## The deployment-packaging constraint

The feedback loop only works if it can catch up.

**Deployments must be packaged such that the program does not run behind its
investment cycle.** If the model refreshes on a cadence and returns lag several
cycles behind the deployment, the loop is open, not closed, and the program
loses the correction it was designed to enforce.

Rules of thumb this implies:

- **Right-size the deployment** so a return signal is expected inside one or
  two model-refresh windows.
- **Instrument the return** at deployment time — the expected metric is
  registered in the model, not chased after the fact.
- **Prefer many small deployments** where each one's return can be attributed,
  over few large deployments where the return is aggregate and the correction
  signal is lost.

## Why after-sales is the right anchor for Richemont

- It is the **most complex transaction** on the estate: serialized
  equipment, multi-decade lifecycle, cross-border routing, cross-system
  reconciliation (SAP CS ↔ Salesforce Service Cloud ↔ Cegid), and multiple
  regulatory retentions (LkSG/CS3D 5-year, GDPR/PIPL deletion, CITES on
  strap materials).
- **Retail sale, clienteling, marketing journey, loyalty accrual, and CPO
  resale are all subsets** of the after-sales transaction — they carry fewer
  fields and fewer constraints.
- **The data already exists** — the equipment master and repair-order history
  are in SAP CS today; the Client 360 View is in Service Cloud today. The
  guess-then-test approach can run against real populations from day one.

Once this superset model is instrumented, deployments across ELEVATE, MDG,
Fashion Management, and the boutique/POS layer all inherit its shape — and
each of them gets the same return-versus-investment feedback loop for free.

---

*Pour le bien-être du peuple.*
