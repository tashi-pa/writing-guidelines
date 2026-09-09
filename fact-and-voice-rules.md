# Fact and voice rules

Applies to anything drafted that another person will read or that describes another person:
outreach and messaging, letters of recommendation, skills assessments, performance and peer
feedback, reviews, references, and any document sent in someone's name.

Both rules below were set after specific failures. They are not stylistic preferences.

Portable copy of the `ty-writing-rules` skill's rules, kept here so they travel to places
without that skill loaded. Where the skill is available, prefer running it directly — it stays
more current than this file.

---

## Rule 1 — Unverified facts are omitted, not hedged

**If a fact is not verified, it does not go in the document at all.**

A hedged claim still lands as a claim. Writing `[unverified guess]` or "reported background"
and letting the reader discount it is not acceptable in anything a third party reads.

| Where | What to do with an unverified fact |
|---|---|
| Outbound copy, letters, assessments, feedback | **Omit entirely.** Write around it |
| Internal working notes | Record the **gap** explicitly: `UNRESOLVED`, `NOT VERIFIED`, `CONTRADICTED`. Recording an absence is not the same as asserting a fact |

**A source is required per claim, not per document.** Before drafting, build a claim ledger:
every factual assertion the text will make, and the source that carries it. A claim with no
source is cut before drafting starts, not softened afterwards.

This applies to URLs too — a link is a claim ("this resource exists and says X"). Fetch it and
confirm it resolves before citing it; a search-result snippet referencing a URL is not the same
as having verified it.

Common failures this catches:

- **Numbers that drifted.** A figure remembered from an earlier draft rather than read from the
  source.
- **Population generalisations.** "Most people...", "that is rarer than it sounds." Unverifiable
  and unnecessary.
- **Inferred intent.** Asserting why someone did something. Ask it as a question instead.
- **Stale press-sourced facts.** Announcements go out of date. Verify against the primary
  source, or omit.
- **Tenure and newness.** Never describe someone as new to a role without a dated record.
- **Dead links.** A URL surfaced by search is not verified until it's been fetched and shown to
  resolve.

---

## Rule 2 — Draft from the source-of-truth voice document, never a generic register

**Before drafting in or for someone's voice, find and read their voice document.** Briefing
file, voice notes, hook library, prior accepted writing samples. Do not compose from a neutral
professional register and hope it passes.

If no voice document exists, say so before drafting rather than inventing one.

**Robotic tells to check for:**

| Tell | Fix |
|---|---|
| Zero contractions across a whole document | Real writing contracts. A paragraph over ~200 characters with no contraction reads machine-written |
| A repeated closing device | Vary it. One device used twice is a template |
| Structural sameness across documents | Run the echo check below |
| Abstract observation instead of a point of view | Lead with a claim about the world; use evidence to support it |
| Identical boilerplate across recipients | Rewrite per recipient |

**Echo check** — run it, don't eyeball it. Across documents of the same kind, compute shared
6-word sequences. Any shared sequence that isn't a required legal/structural phrase is a
template tell.

```python
import re, itertools
def grams(t, n=6):
    w = re.findall(r"[a-z']+", t.lower())
    return {" ".join(w[i:i+n]) for i in range(len(w)-n+1)}
for a, b in itertools.combinations(docs, 2):
    shared = grams(docs[a]) & grams(docs[b])
    if shared: print(a, "<->", b, sorted(shared)[:10])
```

---

## Order of work

1. Locate and read the voice document for whoever the writing is from or about.
2. Build the claim ledger — every assertion, with its source (including every URL). Cut
   unsourced ones now.
3. Draft.
4. Run the echo check across all documents in the set.
5. Check the contraction floor on every paragraph over ~200 characters.
6. Ship the claim ledger alongside the draft, so the reader can audit the evidence without
   re-researching it.

Step 6 matters. A draft that carries its own sources is reviewable; one that does not forces the
reviewer to trust it or redo it.
