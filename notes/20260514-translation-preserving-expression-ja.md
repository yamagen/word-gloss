<!--
https://chatgpt.com/c/69fddc3f-6ebc-83a4-b0c6-e56d6d0a5773
Drive/github/word-gloss/notes/20260514-translation-preserving-expression-ja.md
-->

# 翻訳における言い方の保存と即時文法

Preserving Expression in Translation:
Word-Gloss Annotation and Continuous Reading Translation for Classical Japanese Texts

Last change: 2026/05/14-22:29:58.

Hilofumi Yamamoto, Institute of Science Tokyo
山元啓史、東京科学大学

## 1. 問題

翻訳は意味内容を伝えるが、原文の言い方、順序、照応、息遣いを壊すことがある。
古典本文を翻訳するとき、重要なのは、原文の意味内容を現代語や英語で説明することだけではない。
むしろ、本文に残っている「言い方」が、訳文の中で壊されていないかを確認する必要がある。

もちろん、当時の発話の真実そのものを復元することはできない。
しかし、本文には、語が立ち上がる順序、指示詞の働き、主語を言うか言わないか、歌と地の文の接続、助詞による余情や圧力など、言い方の痕跡が残っている。
翻訳は、それらをすべて再現できるわけではないが、少なくとも訳文によってそれらを不用意に消していないかを検査する必要がある。

そのため、本データでは translation-ja/en-literal, word-gloss, translation-ja/en-natural, translation-ja/en-reading, notes-ja/en を分ける。literal は語対応と時間順を確認するための層であり、word-gloss は語の連鎖を検査可能にする層である。natural は単独の文や歌として自然に読める訳であり、reading は前後の文脈と接続して作品として読み通すための訳である。notes は、本文訳に入れると流れを壊すが、読解や翻訳判断には必要な情報を記録する場所である。

翻訳は、どうしても調整文法側に寄る。訳文として読みやすくするために、主語を補い、語順を整え、関係を説明し、照応を明示するからである。しかし、その調整によって、即時的に立ち上がる原文の言い方が消えてしまうことがある。したがって、翻訳作業では、調整された訳文を作るだけでなく、原文の即時的な連鎖がどこまで残っているかを確認する必要がある。

この作業は、当時の言い方を完全に復元するものではない。むしろ、復元できないからこそ、翻訳が原文の痕跡を壊していないかを理論的に点検するための方法である。

## 2. 方法

literal / word-gloss / natural / reading / notes を分ける。

## 3. 例

伊勢物語 1段 1-3 だけを使う。
「春日の里」->「その里」->「その姉妹」->「この男」
the village of Kasuga -> that village -> the sisters -> This man

## 4. 意義

翻訳結果だけでなく、翻訳が何を壊していないかを検査できる。
