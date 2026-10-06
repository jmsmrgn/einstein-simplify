---
name: einstein-simplify
description: Rewrite technical prose, or your previous response, so a reader outside the field follows it on first read while an expert finds nothing false, only less; or explain a technical topic to a named non-technical reader.
disable-model-invocation: true
argument-hint: "[for <reader>] [text or file, or a topic]"
---

A simple explanation is a teaching order, not a vocabulary swap: the problem before the solution, a picture before the mechanism, the idea before its name. The dual standard: a newcomer follows every sentence on first read, and an expert reading over their shoulder finds nothing false, only less. This skill is for text people read. A request to simplify code is refactoring; say so instead.

## 1. Fix the inputs

- **Source.** The text or file given; with none, your previous response; with a topic instead of text, your own knowledge.
- **Reader.** Named in the request ("for my CFO") is the reader. With none, and the source is your own previous response or text the operator supplied, the reader is the operator: fluent in their own field, not in this one, so nothing factual or actionable is dropped. Otherwise it is a smart adult with no background in the field, stated as a one-line assumption. Invoking this skill overrides any standing instruction that the user is an expert: that instruction describes the operator, and this reader is not an expert in this field.
- **Purpose.** What the reader will do with the text: understand, decide, act, or pass it on. Purpose decides what stays and what comes first.
- **Medium.** Chat reply, document, spoken script, or a message the reader receives.

## 2. Understand it first

State the mechanism to yourself as one causal chain: what happens, why, and why it matters to this reader. Close any gap from the source; with no source the chain is your own knowledge. A gap you cannot close, or a source claim you have specific reason to doubt, is listed for the operator under `Doubted:`, because a gap simplified over becomes a confident error and plainer words make a wrong claim harder to catch, not easier. A doubted claim that stays in the text is attributed to its source; a doubt about your own earlier response is corrected and listed instead.

## 3. Choose the takeaway and the idea budget

Write the one sentence the reader should be able to say back afterwards. Pick the new ideas needed to reach it, three at most, and shrink or cut the rest. Anything the reader needs for their purpose (a risk, a caveat, a choice that is theirs) outranks anything merely interesting. The cap counts unfamiliar ideas in play at once and never licenses dropping what the reader needs; a purpose needing more than three becomes parts, each with its own takeaway.

## 4. Build in teaching order

**Problem, picture, mechanism, name.** When the purpose is to decide or act, open with the answer or the action in one sentence, then explain in this order.

- **Problem.** What goes wrong, or what is hard, without this.
- **Picture.** One concrete example from the reader's world, or one anchor analogy chosen for the single property that has to carry over. Carry it through: each new image costs the reader a reset. The real thing beats any analogy. When an analogy implies something false the reader could act on, say in one clause where it stops holding.
- **Mechanism.** One step at a time. The teachable moment, the step that makes the rest obvious, comes after everything it depends on, and nothing new is introduced until it has landed.
- **Name.** A term arrives after its idea, and only if the reader will meet it again; otherwise the idea stays unnamed.

Contrasts:

- Label first: "RAG, or Retrieval-Augmented Generation, solves..." Teaching order: "The model has never seen your documents. So before it answers, we hand it the few pages that matter. That pattern is called RAG."
- Defined: "cosine similarity (a measure of angular distance between vectors)". Replaced: "how close two passages are in meaning".

## 5. Keep the words plain and fixed

Replace jargon with plain words instead of defining it: a definition asks the reader to hold two words, a replacement gives them one. A term with no everyday equivalent becomes what it measures ("about seven questions in ten"), or a disclosed cut, or a name the reader will meet again, in that order. Give each thing one name and keep it: "passage" here and "chunk" there reads as two things. Keep certainty as found: "probably" stays "probably". Round numbers where precision does not serve the reader's purpose, keeping what they mean.

## 6. The non-technical test

Each line can fail; a self-assessment of followability cannot. Fix a failure, then run them again.

- The takeaway appears in the output in plain words.
- No sentence leans on an idea introduced later.
- Every term an outsider would not use in conversation is replaced, or named after its idea because the reader will meet it again.
- Each part carries three new ideas or fewer.
- Reading as the expert: nothing false, no hedge lost, no doubted claim stated as fact, nothing asserted beyond what the source supports.
- Nothing cut is something the reader needs for their purpose.

## 7. Deliver

- **Chat.** The rewrite alone, in place of the original, then `Assumed:` when the reader was assumed, `Left out:` when something substantive was cut, `Added:` when the rewrite introduces a claim the source does not support, and `Doubted:` for anything you could not stand behind, each omitted when empty.
- **File.** Written into the file when the request says to apply, with the notes in chat; otherwise returned in chat.
- **For a third party.** The finished text, addressed to them, ready to send or say. Operator notes (the labeled lines and analogy limits) sit outside it.
- **Spoken.** Short sentences, no parentheses or brackets, a paragraph break for each pause, the takeaway said again at the close.

`examples/` holds three worked runs: chat rework, a third-party message, a spoken segment. Match their judgment, not their phrasing.
