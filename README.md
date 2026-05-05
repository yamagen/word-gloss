# word-gloss

Last change: 2026/05/05-18:11:03.

Hilofumi Yamamoto, Ph.D.  
Instute of Science Tokyo, Japan

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

Literal translation breaks the moment explanation is added.

Typical triggers include:

- lexical approximation, e.g. `梅壺 -> plum jar`
- structural integration, e.g. `ぬれて -> while`
- subject insertion, e.g. `見て -> watched`
- contextual supplementation, e.g. anticipating later context with `sang`

This repository documents how to avoid such operations and how to preserve word alignment, temporal order, and the signal chain of the original.
