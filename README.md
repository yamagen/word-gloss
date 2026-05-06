# word-gloss

Last change: 2026/05/06-22:21:01.

Hilofumi Yamamoto, Ph.D.  
Institute of Science Tokyo, Japan

![Policy](https://img.shields.io/badge/policy-word--gloss-blue)
![Format](https://img.shields.io/badge/format-JSON%20%2B%20Markdown-green)
![Texts](https://img.shields.io/badge/texts-Classical%20Japanese-lightgrey)
![License](https://img.shields.io/github/license/yamagen/word-gloss)

This repository documents policies and rules for representing classical Japanese texts through multiple layers: word-gloss, literal translation, natural translation, and notes.

The policy is designed for projects such as _Ise Monogatari_ and _Tosa Nikki_, where each text is represented through multiple layers:

- word-gloss
- literal translation
- natural translation
- notes

The main principle is to preserve the observable signal chain of the original text. Word-gloss records the visible sequence of words, morphology, and function, while avoiding explanatory interpretation. Literal translation preserves temporal order and phrase sequence. Natural translation may integrate the expression for readability, but should not unnecessarily close the reader's interpretive space.

## Files

- `gloss-policy.md`: human-readable policy document
- `gloss-policy.json`: machine-readable policy and rule definitions
- `notes/`: methodological notes and examples
- `rules/`: validation rules and operational details

## Core idea

The central principle is simple:

> Literal translation breaks the moment explanation is added.

This does not mean that explanation is unnecessary. Explanation belongs in notes, commentary, or natural translation when appropriate. Word-gloss and literal translation, however, should preserve the observable signal chain before explanatory interpretation is added.

## Example: triggers that break literal translation

Consider the following passage:

```text
むかし、男、梅壺より雨にぬれて、人のまかりいづるを見て、
```

In this project, this passage is treated as a chain of observable signals:

```text
むかし / 男 / 梅壺より / 雨にぬれて / 人のまかりいづるを / 見て
```

In English, the units are placed in the same sequence without being integrated into a completed sentence:

```text
Once upon a time, a man, from Ume-tsubo, getting wet in the rain, seeing people going out,
```

The following operations break the literal translation:

- Lexical approximation: `梅壺 -> plum jar`
  `梅壺` is a proper name for a place in the court. Translating it as `plum jar` replaces a proper noun with a familiar lexical approximation.

- Structural integration: `雨にぬれて -> while getting wet in the rain`
  The original presents a phrase in sequence, but `while` integrates it into a subordinate construction.

- Predication: `見て -> watched`
  `見て` is an open conjunctive form leading to what follows. Translating it as `watched` turns it into a completed predicate.

- Contextual supplementation: adding `sang` by anticipating the following poem
  The passage has not yet stated that anyone sang or composed a poem. Adding `sang` introduces information from later context.

This repository documents how to avoid such operations and how to preserve word alignment, temporal order, and the signal chain of the original.

## Signal and interpretation

This project distinguishes between observable signals and interpretations constructed from context.

Word-gloss records the visible sequence of forms, morphology, and functions. It does not encode interpretations that belong to the receiver's reading of the context. For example, a particle or auxiliary may produce a wish-like or exclamatory reading in a given context, but such interpretation is not automatically treated as the fixed meaning of the form itself.

Interpretive readings are handled in natural translation or notes, not forced into the word-gloss layer.

## Literal translation and natural translation

Literal translation preserves the temporal order and phrase sequence of the original. It may look fragmentary as a completed sentence, but such phrasing can still be natural as a chain of speakable units.

Natural translation may integrate the expression for readability. However, it should avoid unnecessary additions and should not close interpretive space that the original leaves open for the reader.

## License

See `LICENSE`.
