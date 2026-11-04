# MLBB 日本語図鑑 — データ保守メモ

更新：2026-11-04（日本時間）。公開ページ：`https://kyavet.com/mlbb/`、本体：`mlbb/index.html`。GitHub への反映は確認済み。公開 URL の外部到達確認は別途実施する。

## 現在の収録と進捗

- 収録 134件：通常サーバー133体＋Advanced Server の Dori（`isPlayable:false`）1体。**134体実装済みとは表現しない**。
- `guide` の固有メモ：16件。`verified` の個別資料照合：10件（全Lvの実機検証完了という意味ではない）。
- 全件で名前・役割・日本語効果要約・レーン等を収録。パッチ別のスキル係数・装備・対面統計・固有動画の網羅は**未完**。
- データの単一ソースは `<script id="embedded" type="application/json">…</script>` に格納された134件。実行時に `const H=JSON.parse(document.getElementById('embedded').textContent)` で参照。旧版のように JSON と JavaScript に二重記載しない。

## 検証の優先順位

1. 最新の公式告知・ゲーム内説明・Original Server パッチノート。
2. 日付・バージョン明記の再録パッチ資料（[MLBBHub](https://mlbbhub.com/patch-notes)、[MOBAログ](https://moba-log.com/mlbb/patch-notes/)）。
3. [MLBBDex API](https://mlbbdex.com/en/api-doc)（Mobile Legends Wiki 由来、CC BY-SA。参照元を明記）。`/api/v1/heroes/{slug}` は原文確認用。通信/CORS 制限を考慮する。
4. [MLBB Guides](https://www.mlbbguides.com/) 等は個別ビルドの参考。統計は集計期間・ランク・パッチ・サンプル数が分からなければ断定しない。

「確認日」と「その資料が対象とするパッチ日」は別に記録する。2026-11-04時点で把握した直近の Original Server は **2.2.16a (2026-10-14)**、Advance Server の参照は **2.2.30 (2026-10-30)**。最新保証ではない。後者の調整を現在のランクマッチに反映済みと書かない。

## 個別ヒーローの増強ルール

- `skills` はパッシブ・各技の4件（特殊なキャラは名称・実際の技構造を明記）。数値は**レベル範囲 / 物理・魔法攻撃係数 / 秒数 / CD / MP / パッチ / 出典**を併記。
- `guide` の `combo`, `numbers`, `items`, `emblem`, `spell`, `good`, `bad`, `sources` を資料の範囲で追記。ビルドは相手やパッチの条件を添える。
- `verified` は一次資料・信頼できる出典と照合した項目のみ設定。作成日をもって「検証済み」としない。
- 適性は EXP / JG / MID / GOLD / ROAM の5レーンを主・兼任・未検証で分ける。未検証 ≠ 不適性。
- 相性は対面キャラ名・レーン・パッチ・データ/戦術上の理由を提示。根拠のない相性ランキングは禁止。
- 動画は実在する ID・投稿者・対象バージョンを確認して `curatedVideos` に入れる。古い版/Advance Serverは明示。確認できない動画 ID を仮置きしない。
- 画面内で完結するように `details` の折りたたみ形式を保ち、スマホで確認する。404/スクリプト構文エラーがないか検証する。
- 公開成功は GitHub コミットだけでなく、Pages と `kyavet.com/mlbb/` の到達確認を別記。

## 更新状況（2026-11-04）

- Kaja（2.1.95）、Masha・Bruno（2.2.16）の大規模リメイク後の効果を修正。
- Doriを通常サーバーから分け、先行版のパッシブ・3スキルと2.2.30変更候補を掲載。
- 2.2.16aで調整された Kalea・Aulus・Hirara・Eudora・Rafaela にパッチ履歴を追記（全係数は未確認）。
- 数値を「資料で確認した変更値」と「最新の全レベル確定値」に分けて示す。

## 次回の優先課題

1. 通常サーバー2.2.16aの個別変更数値を5体に反映し、後続Original Server更新を再確認。
2. `quality:"効果要約"` のキャラのうち、Joy, Natalia, Atlas, Carmilla, Diggie, Gloo, Melissa, Helcurt等を優先してスキル係数・対面・ビルド・動画を検証。
3. 全ヒーローを五十音/英字と検索から検査し、リンク切れ・重複・旧技名を取り除く。
4. **全キャラの情報が検証できるまで契約書の編集には移行しない。**
