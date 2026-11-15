# skills

## connpass-page-builder

Markdownのイベント情報を意味に応じて通常セクション、タイムテーブル、登壇内容に分類し、connpassの「イベントの説明」欄用HTMLを生成するAgent Skillです。ユーザーがconnpassで表示調整したHTMLから3種類のテンプレートを抽出しています。見出し名やセクション数を固定せず、入力の内容に応じて選び、元の順番で組み合わせます。

### インストール

Skills CLIで個別にインストールできます（この変更がGitHubに反映された後）。

```sh
npx skills add bells17/skills --skill connpass-page-builder -a codex
```

グローバルインストール:

```sh
npx skills add bells17/skills --skill connpass-page-builder -a codex -g
```

### 使い方

```text
$connpass-page-builder
event.md からconnpass用HTMLを生成してください。
```

ファイル指定の代わりに、チャットにMarkdownを貼り付けても使えます。

```text
$connpass-page-builder
色味: 緑系
全体の記号: ◆
セッションの記号: 🎤
Markdown:
# イベント概要
参加者同士で知識や経験を共有するミートアップです。
```

| 入力 | 必須 | 省略時 |
| --- | --- | --- |
| Markdown（貼り付け・ファイル） | はい | 未指定時のみ提供を依頼 |
| 色味（自然言語・HEX） | いいえ | Blue |
| 全体の記号（Unicode・絵文字） | いいえ | ☸ |
| セッションの記号（Unicode・絵文字） | いいえ | ▸ |

BlueはPrimary `#28679B`、Accent `#326CE5`、Navy `#24344B`、Border `#B8D6F0`。色味には「落ち着いた緑系」「明るいオレンジ系」や「Primary: #28679B、Accent: #326CE5」も指定できます。色指定だけでレイアウトは変更しません。

生成されたHTMLコードブロックの中身だけをコピーし、connpassのイベント編集画面にある「イベントの説明」欄へ貼り付け、プレビューで確認してください。コードフェンス（```htmlなど）は含めません。画像、表、記号、スマートフォンでの表示を確認してから保存・公開してください。Skillが自動投稿することはありません。

再編集は「写真を120pxにして」「全体の青を少し暗くして」などと指示できます。指定箇所だけを変更し、HTML全体を再出力します。

**実行スクリプトは同梱していません。** SkillはMarkdown定義、HTMLテンプレート、参考Markdownだけで構成され、通常の生成にコマンド実行・ネットワークアクセス・外部サービスは不要です。指定ファイルと同梱資料を読み取れるエージェント環境を使ってください。インストール時のSkills CLIにはNode.js/npmとネットワークが必要です。

### 資料と検証

- [Skill定義](skills/connpass-page-builder/SKILL.md)
- テンプレート：[その他](skills/connpass-page-builder/templates/standard.html)・[タイムテーブル](skills/connpass-page-builder/templates/timetable.html)・[登壇内容](skills/connpass-page-builder/templates/session.html)
- [ブロック仕様](skills/connpass-page-builder/references/block-types.md)
- [connpass互換性](skills/connpass-page-builder/references/connpass-compatibility.md)
- [架空イベントのサンプルMarkdown](skills/connpass-page-builder/references/sample-input.md)
- [検証ケースと結果](skills/connpass-page-builder/references/validation.md)

connpassによるタグ・属性の除去や表示環境の違いがあるため、生成結果のconnpass上での表示一致は保証しません。
