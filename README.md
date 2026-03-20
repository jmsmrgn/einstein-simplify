# einstein-simplify

> "If you can't explain it simply, you don't understand it
> well enough." — Albert Einstein

A Claude skill that rewrites complex technical content so a
non-technical person sitting next to an expert can follow every
word — without losing accuracy or depth.

## Install

```bash
npx skills add jmsmrgn/einstein-simplify
```

## What it does

Takes any dense technical explanation, presentation script,
documentation, or demo and rewrites it through seven structural
principles:

1. **Concept before label** — never name a thing before the concept exists in the listener's head
2. **Analogy before description** — ground it before you explain it
3. **One worked example** over four shallow surface descriptions
4. **No acronyms** until the concept is established
5. **Replace jargon**, don't define it — definitions ask the listener to hold two words in mind
6. **Give the teachable moment full space** — find it, slow down, let it land
7. **Non-technical observer test** on every section before moving on

This is structurally different from "simplify your writing" tools.
It fixes the _order_ in which ideas are introduced — which changes
the entire experience of understanding.

## Before / After Examples

- [Vector Embeddings (RAG)](examples/before-after-rag.md)
- [Kubernetes](examples/before-after-kubernetes.md)

## Works on

- Technical presentations and demo scripts
- Customer-facing documentation
- Engineering RFCs written for non-engineers
- Onboarding and training materials
- Investor pitches for technical products
- Medical or legal explanations for non-specialists
- Anything where someone in the room might not follow

## Usage

Describe your task naturally — Claude will recognize when to
apply this skill. Or invoke directly:

> "run einstein-simplify on this"
> "simplify this for a non-technical audience"
> "make this ELI5"

## License

MIT
