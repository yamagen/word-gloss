<!--
https://chatgpt.com/c/69e43a6d-4a3c-83ab-a116-55de5ca7d98d
gloss-policy.md
-->

# Word-gloss Policy for Classical Japanese Translation

Last change: 2026/05/05-17:01:06.

Hilofumi Yamamoto, Ph.D.  
Instute of Science Tokyo, Japan

## 1. 基本方針

本プロジェクトの word-gloss は、原文に現れている信号の連鎖を記述するためのものである。したがって、語の意味を文脈に基づいて説明的に確定するのではなく、観察可能な語形、語順、形態、機能をできるだけ原子的に記録する。

word-gloss は自然訳ではない。読者が文脈から構成する解釈を、word-gloss に先取りして入れない。

## 2. 三層構造

本プロジェクトでは、翻訳と注釈を次の三層に分ける。

- word-gloss: 語対応と信号の連鎖を保持する
- translation-en / translation-ja: 原文の時間順を保つ逐語訳
- translation-en-natural / translation-ja-natural: 読みやすい自然訳

この三層を混同しない。

## 3. word-gloss のフィールド

各語は原則として次のフィールドを持つ。

```json
{
  "word": "出現形",
  "lemma": "辞書形",
  "kana": "出現形の読み",
  "lemma-kana": "辞書形の読み",
  "romaji": "出現形のローマ字",
  "lemma-romaji": "辞書形のローマ字",
  "gloss": "原子的gloss.形態情報",
  "pos": "品詞",
  "ku": 0
}
```

和歌では `ku` に 1 から 5 の句番号を入れる。和歌でない地の文では `ku: 0` とする。

## 4. word と lemma

`word` は原文に現れている形を保持する。
`lemma` は語彙同定のための辞書形を入れる。

たとえば、原文が「むすび」であっても、意味として「掬ぶ」である場合は次のようにする。

```json
{
  "word": "むすび",
  "lemma": "掬ぶ",
  "kana": "むすび",
  "lemma-kana": "むすぶ",
  "romaji": "musubi",
  "lemma-romaji": "musubu",
  "gloss": "scoop.ADV",
  "pos": "V",
  "ku": 3
}
```

原文表記は壊さず、lemma で語義を特定する。

## 5. gloss の原則

gloss は短く、原子的にする。説明文を入れない。

避ける例:

```json
"gloss": "(accusative particle)"
"gloss": "to (DAT)"
"gloss": "said-to-be"
```

推奨:

```json
"gloss": "ACC"
"gloss": "DAT"
"gloss": "say.ATTR"
```

gloss-line では `.` の前だけを表示するため、ひとまとまりとして表示したい英語はハイフンでつなぐ。

```json
"get-wet.ADV"
"rely-on.ADV"
"all-the-more"
"jeweled-water"
```

`get.wet.ADV` のように書くと、表示時に `get` だけになるため避ける。

## 6. pos と gloss の分離

`pos` は品詞・構造を示す。
`gloss` は意味・機能・形態を示す。

例:

```json
{ "word": "ども", "gloss": "PL.SUF", "pos": "SUF" }
{ "word": "げ", "gloss": "look.SUF", "pos": "SUF" }
```

`SUF` が gloss と pos の両方に現れることは許容する。pos 側の `SUF` は品詞、gloss 側の `SUF` は機能を示す。

## 7. 形態情報

活用形は gloss の後ろに `.ADV`, `.ATTR`, `.IRR`, `.REALIS`, `.IMP` などを付けて示す。

例:

```json
"live.ADV"
"PST.ATTR"
"exist.IRR"
"nonexist.ATTR"
"attach.IMP"
```

ただし、形態情報は見えている連鎖に基づいて付ける。解釈によって補わない。

## 8. 助動詞

助動詞は原則として `AUX` とする。

例:

```json
{ "word": "けり", "gloss": "PST", "pos": "AUX" }
{ "word": "けれ", "gloss": "PST.REALIS", "pos": "AUX" }
{ "word": "む", "gloss": "FUT", "pos": "AUX" }
{ "word": "し", "lemma": "き", "gloss": "PST.ATTR", "pos": "AUX" }
```

助動詞の詠嘆・余韻などは、word-gloss に直接入れず、必要に応じて notes に記述する。

## 9. 解釈を入れない

word-gloss は、送り手から出ている信号の記述である。受け手が文脈から構成する解釈を word-gloss に入れない。

例:

```json
{ "word": "なむ", "gloss": "EMPH", "pos": "P" }
```

「なむ」は文脈上、願望的に訳されることがある。しかし、word-gloss では固定的に `DES` とせず、強調要素として `EMPH` とする。願望的解釈は自然訳または notes で扱う。

## 10. 固有名詞

地名・人名・宮中の場所名などは `PN` とする。

例:

```json
{ "word": "梅壺", "gloss": "Ume-tsubo", "pos": "PN" }
{ "word": "深草", "gloss": "Fukakusa", "pos": "PN" }
{ "word": "山城", "gloss": "Yamashiro", "pos": "PN" }
```

固有名詞を説明的に英訳しない。

避ける例:

```json
"梅壺" -> "plum jar"
"深草" -> "deep grass"
```

## 11. 「てふ」の処理

「てふ」は必要に応じて「て」＋「ふ」に分ける。

```json
{ "word": "て", "gloss": "CONJ", "pos": "P" },
{ "word": "ふ", "gloss": "say.ATTR", "pos": "V" }
```

これは「てふ」を「といふ」の縮約として見ながら、見えている連鎖を保持するための処理である。

## 12. 「ものを」などの連語

「ものを」は常に一括して詠嘆表現とは扱わない。
原則として、見えている形に従い、

```json
{ "word": "もの", "gloss": "thing", "pos": "N" },
{ "word": "を", "gloss": "ACC", "pos": "P" }
```

のように分ける。
詠嘆・余情・逆接的余韻は、文脈から立ち上がる場合に notes で扱う。

## 13. 逐語訳との関係

word-gloss は逐語訳の基礎である。
逐語訳では、word-gloss の語順と信号の連鎖をできるだけ保持する。

逐語訳を崩す代表的なトリガーは次の通りである。

- 語彙の近似: 梅壺 -> plum jar
- 文の統合: ぬれて -> while
- 主語の導入: 見て -> watched
- 文脈補完: 後続を先取りして sang を入れる

説明したくなった瞬間に、逐語訳は壊れる。

## 14. 自然訳との関係

自然訳では、読みやすさのために統合を行ってよい。
ただし、原文にない情報を過度に補わない。読者が想像すべき余地を訳者が先に閉じない。

例:

```text
なき世なりけり
```

を「二人の間柄でしたね」と訳すと、原文の「世」の広がりが閉じる。
本プロジェクトでは、「その甲斐もない世でしたね」のように、原文の語をできるだけ残す。

## 15. abbreviations

略号表は、各エントリで実際に使用している gloss を閉じるために置く。最低限、使った略号は必ず定義する。

よく使う略号:

```json
{
  "ACC": "accusative particle",
  "ADJ": "adjective",
  "ADV": "adverbial form",
  "ATTR": "attributive form",
  "AUX": "auxiliary",
  "COND": "conditional particle",
  "CONJ": "conjunctive particle",
  "DAT": "dative particle",
  "DET": "determiner",
  "EMPH": "emphatic particle",
  "FUT": "modal auxiliary",
  "GEN": "genitive particle",
  "HON": "honorific",
  "IMP": "imperative form",
  "INTJ": "interjection",
  "IRR": "irrealis form",
  "N": "noun",
  "NEG": "negative auxiliary",
  "NMLZ": "nominalizer",
  "P": "particle",
  "PERF": "perfect auxiliary",
  "PFX": "prefix",
  "PL": "plural",
  "PN": "proper noun",
  "PST": "past auxiliary",
  "Q": "question particle",
  "QUOT": "quotative particle",
  "REALIS": "realis form",
  "SUF": "suffix",
  "TOP": "topic particle",
  "V": "verb"
}
```
