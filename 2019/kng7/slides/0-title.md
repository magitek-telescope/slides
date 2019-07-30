<!-- classes: title -->

## 気軽な Node.js バックエンド開発には TypeORM がちょうどいい

<p>
  2019.08.02 #kng7 / LINE株式会社 UIT室 花谷拓磨(@potato4d)
</p>

---

## 自己紹介

- 花谷拓磨(@potato4d)
- Working at...
  - LINE株式会社 UIT室 / Developer Relations室
-

---

## Agenda

- 結局俺たちは O/R Mapper に何を求めているのか
- TypeScript ベースで「ちょうどいい」 TypeORM の紹介
  - ActiveRecord パターンと Repositoryパターンの段階的な移行が可能

---

## みなさん ORM は好きですか？

---

## 何が便利で何が不便ですか？

---

## 実はみなさんの言う問題点って<br/>「ActiveRecord かどうかが排他なこと」<br/>に起因していませんか？

---

## 結局俺たちは O/R Mapper に何を求めているのか

### ORM を使うなら ActiveRecord で雑に作りたい

- 開発初期はデータ構造やリレーションにドラスティックな変更が入りやすい
  - できれば高速に対処したい
- 初期の CRUD くらいは爆速で作ってしまいたい
  - プロトタイピングの速度は落としたくない
-

---

## 結局俺たちは O/R Mapper に何を求めているのか

### ActiveRecord で作ったものをメンテし続けたくない

- とはいえ継続的に Model = DB みたいな状態で運用したくない
  - この辺りが年季の入った Rails が嫌われやすい点な気がする
- 段階的に Repository パターンを適用できるような世界観が欲しい
  - DAO を DAO として用意した上でより抽象度の高い実装に落とし込みたい
  - はじめからやると早すぎる最適化感があるので折を見て調整したい

---

## 結局俺たちは O/R Mapper に何を求めているのか

### 気合を入れたり入れなかったりしたい

- はじめは雑に作れると嬉しい
- 徐々にしっかりしていくことが不可能だと嬉しくない

---

## そんなものなくない？

---

## <img src="https://raw.githubusercontent.com/typeorm/typeorm/master/resources/logo_big.png" />

---

## TypeScript ベースで「ちょうどいい」 TypeORM の紹介

---

## TypeORM の特徴

- TypeScript 向けの ORM (JavaScript 対応)
  - MySQL, PostgreSQL, SQLite から MongoDB まで対応
- GitHub Star も 15k+ と注目度の高い ORM
  - https://github.com/typeorm/typeorm
  - ちなみに NPM の weekly downloads は 100k+

---

## TypeORM の特徴

- デコレータベースの簡潔かつ TypeSafe なエンティティ定義と
- 柔軟かつ便利な Migration
- ActiveRecord と Repository にどちらも対応

---

## TypeORM のうれしいところ

- デコレータベースの簡潔かつ TypeSafe なエンティティ定義と

---

## TypeORM のうれしいところ

- 柔軟かつ便利な Migration

---

## TypeORM のうれしいところ

- ActiveRecord と Repository にどちらも対応

---

## TypeORM の活用シチュエーション

---

## TypeORM の活用シチュエーション

- LINE UIT室の場合
  - Podcast UIT INSIDE の API サーバーで使っています
- UIT INSIDE の立ち上げ時の場合
  - Express + TypeORM で TypeScript な Node.js サーバーを運用
  - 初期リリースまでは高生産性の恩恵を存分に受ける
    - 公開前までは自動マイグレーションで開発
    - データモデルは極力 ActiveRecord で実装

---

## TypeORM の活用シチュエーション

- 立ち上げ後機能改修を加えていく場合
  - ここからは非 LINE プロジェクトでの体験の話
  - 直で ActiveRecord を使わずとも Repository に切り替えて queryBuilder も使いつつ運用できることに気づいていく
    - 徐々に ActiveRecord による実装が辛くなっていくので移行していく
    - もちろん全部ができるわけではないが、割れ窓となりうるコードを排除しつつ前進
      - これまでの ORM ではできなかった戦略のとり方で嬉しい！

---

## おわりに

---

## おわりに

- TypeORM はプロダクトと共に成長していける手軽な ORM
  - Rapid Development のための土壌と堅牢な設計のための布石がどちらも揃っている
  - はじめから厳格に実装するもよし、あとから切り出すもよしな柔軟な仕様
  - 決して全ての機能が Simple とは言えないが、 Simple / Easy どちらにも寄せられる

---

## おわりに

- ORM 好き派嫌い派みたいな概念は必要ない
  - 好き嫌いじゃなくているか要らないかで選ぶんだよ
  - ORM というざっくりしたものではなくて何が不満で何が便利化を言語化してみる
