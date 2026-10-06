# einstein-simplify

> "If you can't explain it simply, you don't understand it well enough." Attributed to Albert Einstein.

A skill that rewrites technical prose so a reader outside the field follows it on first read, while an expert reading over their shoulder finds nothing false, only less.

## Install

```
npx skills add jmsmrgn/einstein-simplify
```

## What it does

Most "simplify this" tools fix word choice. This one fixes the order in which ideas are introduced, which is where most of the gain is.

A simple explanation is a teaching order. The rewrite is built in four stages: the problem before the solution, one picture before the mechanism, the mechanism one step at a time, and a name only once its idea exists and only if the reader will meet it again. Concept before label, analogy before description, and no acronyms until the concept lands are the three older rules that sequence absorbs; the teachable moment is the step the mechanism has to land on.

Two things bound it. The reader leaves with one takeaway, carried by at most three new ideas at once; everything else is cut or shrunk to a clause, and anything the reader needs in order to decide or act outranks anything merely interesting. And accuracy is "nothing false, only less": an expert finds omissions but no errors, hedges stay hedges, numbers keep their meaning, and cuts are disclosed.

## Usage

```
/einstein-simplify <text>              rework this text, or your previous response
/einstein-simplify for my CFO <text>   write for a named reader
```

The skill sets `disable-model-invocation: true`, so it is invoked by name and never fires on its own. It is for explanations people read, not for refactoring code.

In chat the output is the rewrite, followed by whichever of four labeled lines has content: `Assumed:` the reader it assumed, `Left out:` substantive cuts, `Added:` claims the source does not support, `Doubted:` anything it could not stand behind, a source claim it believes wrong among them. When the rewrite goes into a file, those lines still come back in chat.

## Works on

- Talks, demos and scripts for audiences of mixed background
- Investor and customer-facing explanations of technical products
- Engineering RFCs read by non-engineers
- Onboarding and training material
- Medical or legal explanations for non-specialists
- Reworking a dense answer until the person who asked can act on it

## Examples

Three worked runs, each showing its inputs, takeaway, idea count, output, labeled lines, and why it looks the way it does:

- [Chat rework](examples/chat-rework.md)
- [A message for a non-technical third party](examples/message-for-third-party.md)
- [A spoken script segment](examples/spoken-script.md)

## License

MIT
