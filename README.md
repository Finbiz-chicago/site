<p align="center"><img src="docs/banner.png" alt="" width="100%"></p>

<h1 align="center">site</h1>
<p align="center"><em>The public face of FinBiz, at <a href="https://finbiz.cloud">finbiz.cloud</a>. Generated HTML and nothing else.</em></p>

---

This repository holds **no source, no raw data and no secrets**. It receives HTML produced from
the packages in the private `scraper` repository, and receives it in one direction only. What
is publicly visible is therefore never an accident: it is only ever what a command deliberately
produced.

Editing a page here would be overwritten by the next build.

## What the site contains

- what FinBiz is, in one page
- how the repositories fit together, and which one to open
- the interfaces: what each system receives, returns and guarantees
- how to run the stack from an empty clone
- the directory itself, read-only

Five pages, about fifteen minutes end to end. It is written for a developer arriving with no
context.

## The rule it publishes under

> A service appears only if it comes with a quote of at least eight words, present word for
> word on a page belonging to the organisation that provides it, together with the link.

The build **refuses to write anything at all** if it finds a service that breaks this. That is
not a guideline enforced by care; it is a check that stops the build.

What does not clear the bar is not deleted. It is set aside and counted on the page itself:
services excluded by written decision, services withheld because the quote is a paraphrase, and
organisations awaiting a confirmation only they can give.

## How it is published

From the `scraper` repository:

```bash
cd site
./publish.sh --dry-run     # regenerate and check, publish nothing
./publish.sh               # regenerate, check, commit, push
```

That procedure refuses to publish if a publication rule breaks, if the two independent checks
disagree on the number of services, or if the leak scan finds anything new. It also preserves
this repository's own files, and will not attach a custom domain before DNS actually points
here — both lessons learned the hard way.

## Checking it

```bash
gitleaks detect --source . --no-git --redact --baseline-path .gitleaks-baseline.json
```

The baseline records the one known detection: a long string inside a passage quoted from Rogers
Park Business Alliance's own website. Any **new** detection still reports. The baseline and the
scan must use the same options, `--redact` included — a fingerprint includes the matched value.
