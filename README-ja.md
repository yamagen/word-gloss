# word-gloss

Last change: 2026/05/06-22:25:30.

山元啓史  
東京科学大学

![方針](https://img.shields.io/badge/policy-word--gloss-blue)
![形式](https://img.shields.io/badge/format-JSON%20%2B%20Markdown-green)
![対象](https://img.shields.io/badge/texts-Classical%20Japanese-lightgrey)
![License](https://img.shields.io/github/license/yamagen/word-gloss)

この repository は、古典日本語テキストを word-gloss, 逐語訳, 自然訳, notes の複数層で記述するための方針と規則を管理するものです。

主な対象は、『伊勢物語』『土佐日記』などの古典日本語テキストです。各テキストは、以下の層に分けて扱います。

- word-gloss
- 逐語訳
- 自然訳
- notes

本 repository の基本方針は、原文に現れている観察可能な信号の連鎖を保持することです。word-gloss は、原文の語順、語形、形態、機能を記録するための層であり、文脈から構成される解釈を先取りして入れません。逐語訳では、原文の時間順と句の連鎖を保持します。自然訳では、読みやすさのために統合を行いますが、原文にない情報を過度に補わず、読者が意味を立ち上げる余地を不必要に閉じないことを重視します。

## Files

- `gloss-policy.md`: 人間が読むための方針書
- `gloss-policy.json`: 機械処理・検証用の方針と規則
- `notes/`: 方法論的な注記と例
- `rules/`: 検証規則と運用上の細則

## Core idea

中心となる原則は単純です。

> 逐語訳は、説明を加えた瞬間に崩れます。

これは、説明が不要であるという意味ではありません。説明は、必要に応じて notes, commentary, 自然訳に置きます。しかし、word-gloss と逐語訳では、説明的解釈を加える前に、観察可能な信号の連鎖を保持することを優先します。

## Example: 逐語訳を崩すトリガー

たとえば、次の原文を考えます。

```text
むかし、男、梅壺より雨にぬれて、人のまかりいづるを見て、
```

本プロジェクトの逐語訳では、この箇所を次のような信号の連鎖として扱います。

```text
むかし / 男 / 梅壺より / 雨にぬれて / 人のまかりいづるを / 見て
```

英語でも、完成文に統合せず、次のように順に置きます。

```text
Once upon a time, a man, from Ume-tsubo, getting wet in the rain, seeing people going out,
```

これに対して、次のような操作を加えると、逐語訳は崩れます。

- 語彙の近似：`梅壺 -> plum jar`
  `梅壺` は宮中の場所名です。これを `plum jar` と訳すと、固有名詞を通常語に置き換えてしまいます。

- 文の統合：`雨にぬれて -> while getting wet in the rain`
  原文では句が順に並んでいますが、`while` を入れると従属節として統合されます。

- 述語化：`見て -> watched`
  `見て` は後続へつながる連用的な形ですが、`watched` とすると完結した述語になり、原文の宙づりの連鎖が失われます。

- 文脈補完：後続を先取りして `sang` を入れる
  この箇所にはまだ「詠む」「歌う」は出ていません。後続の歌を先取りして `sang` を入れると、観察可能な信号を越えた補足になります。

本 repository では、これらの操作を避け、語対応、時間順、原文の信号の連鎖を保持する方法を記述します。

## Signal and interpretation

本プロジェクトでは、観察可能な信号と、文脈から構成される解釈を区別します。

word-gloss は、見えている語形、語順、形態、機能を記録します。受け手が文脈から構成する解釈を、word-gloss に固定的な意味として埋め込みません。たとえば、ある助詞や助動詞が文脈上、願望的・詠嘆的に解釈される場合があっても、それをその形式自体の固定的意味として自動的に扱うことはしません。

解釈的な読みは、word-gloss ではなく、自然訳または notes で扱います。

## Literal translation and natural translation

逐語訳では、原文の時間順と句の連鎖を保持します。完成文として見ると断片的に見える場合がありますが、そのような表現も、発話可能な単位の連鎖としては自然に成立します。

自然訳では、読みやすさのために統合を行ってよいものとします。ただし、原文にない情報を過度に補わず、原文が読者に残している解釈の余地を不必要に閉じないことを重視します。

## Directory structure

```text
word-gloss/
├── LICENSE
├── README.md
├── README-ja.md
├── gloss-policy.md
├── gloss-policy.json
├── notes/
└── rules/
```

## notes

`notes/` には、個別の判断や方法論的なメモを置きます。

例：

- 「なむ」を固定的な願望表現とせず、EMPH とする理由
- 「ものを」を常に詠嘆表現としない理由
- 「てふ」を分解する場合の扱い
- 説明を加えることで逐語訳が崩れる例
- 読者の解釈余地を閉じない翻訳

## rules

`rules/` には、将来的に検証可能な規則を置きます。

例：

- 使用可能な略号
- 必須フィールド
- lemma と word の関係
- gloss の形式
- `ku` の使い方
- 和歌と地の文の区別

## License

`LICENSE` を参照してください。
