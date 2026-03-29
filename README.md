# Business Tools Plugin for Claude Code

製造業向け週報作成と見積書PDF生成をバンドルした Claude Code プラグインです。

---

## 機能

### 製造週報（weekly-report）
- 生産実績を QCD（品質・コスト・納期）の観点で整理
- KPI カード（合計生産数・不良率・設備稼働率・計画達成率）を自動算出・色分け
- Chart.js によるグラフ付き HTML レポートを出力

### 見積書作成（estimate-generator）
- Web 制作向けデフォルト単価テーブル内蔵（デザイン・コーディング・WordPress・動画等）
- ヒアリング → 確認 → PDF 生成のワークフロー
- WeasyPrint による A4 PDF 出力（HTML フォールバック付き）

---

## スラッシュコマンド

| コマンド | 説明 |
|---------|------|
| `/business-tools:weekly-report` | 製造週報を作成 |
| `/business-tools:estimate-generator` | 見積書 PDF を作成 |

---

## インストール

### 1. マーケットプレイスを追加

```
/plugin marketplace add business-tools/claude-code-business-tools-plugin
```

### 2. プラグインをインストール

```
/plugin install business-tools-plugin@business-tools-marketplace
```

### 3. Claude Code を再起動

スキルとコマンドが有効になります。

---

## 前提条件

### 見積書 PDF 生成

PDF 出力には以下が必要です:

- **uv** (Python パッケージランナー)
- **WeasyPrint** (`uv run --with weasyprint` で自動インストール)
- macOS の場合: `brew install pango`

PDF 生成に失敗した場合でも HTML ファイルが出力されるため、ブラウザの「PDF として印刷」機能で代用できます。

### 週報

追加の依存関係はありません。Chart.js は CDN から読み込まれます。

---

## ディレクトリ構成

```
claude-code-business-tools-plugin/
├── .claude-plugin/
│   ├── plugin.json          # プラグインメタデータ
│   └── marketplace.json     # マーケットプレイス設定
├── README.md
├── commands/
│   ├── weekly-report.md     # 週報スラッシュコマンド
│   └── estimate-generator.md # 見積書スラッシュコマンド
└── skills/
    ├── weekly-report/
    │   ├── SKILL.md          # 週報スキル定義
    │   └── templates/
    │       └── report-template.html
    └── estimate-generator/
        ├── SKILL.md          # 見積書スキル定義
        ├── references/
        │   └── price_table.md
        ├── scripts/
        │   └── generate_estimate_pdf.py
        └── evals/
            └── evals.json
```

---

## ライセンス

MIT
