<!-- language -->
[English](README.md) | [简体中文](README_zh-CN.md) | [Русский](README_ru.md) | [日本語](README_ja.md) | [한국어](README_ko.md) | [Français](README_fr.md) | [Deutsch](README_de.md) | [Italiano](README_it.md)| [Español](README_es.md) | [Português](README_pt.md) | [العربية](README_ar.md) | [ไทย](README_th.md) | [Tiếng Việt](README_vi.md)

# gstack

> 「おそらく 12 月以降、コードを一行も入力していないと思います。これは非常に大きな変化です。」— [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/)、No Priors ポッドキャスト、2026 年 3 月

Karpathy がこれを言うのを聞いて、私はそれがどのように可能なのかを知りたくなりました。一人の人がどのようにして 20 人のチームのようにプロダクトを届けられるのか？Peter Steinberger は [OpenClaw](https://github.com/openclaw/openclaw) を構築しました — GitHub で 247K のスター — 本質的に AI エージェントだけで。革命はここにあります。正しいツールを持つ一人のビルダーは、従来のチームよりも速く動けます。

私は [Garry Tan](https://x.com/garrytan)、[Y Combinator](https://www.ycombinator.com/) の社長兼 CEO です。私は何千ものスタートアップ — Coinbase、Instacart、Rippling — と一緒に働いてきました — それらがガレージに 1 人か 2 人いた頃からです。YC 之前は、Palantir で最初のエンジニア/PM/デザイナーの一人であり、Posterous を共同設立（Twitter に売却）、YC の内部ソーシャルネットワーク Bookface を構築しました。

**gstack が私の答えです。** 私は 20 年間プロダクトを構築してきましたが、今ほど多くのコードを届けたことはありません。過去 60 日間で：**600,000+ 行の本番コード**（35% はテスト）、**1 日あたり 10,000-20,000 行**、パートタイムで、YC をフルタイムで運営しながら。これは 3 つのプロジェクトでの最後の `/retro` です：**1 週間で 140,751 行追加、362 コミット、約 115k 行の正味 LOC**。

**2026 年 — 1,237 回の貢献、そして増加中：**

![GitHub 貢献 2026 — 1,237 回の貢献、1-3 月に大幅加速](docs/images/github-2026.png)

**2013 年 — YC で Bookface を構築していた頃（772 回の貢献）：**

![GitHub 貢献 2013 — YC で Bookface を構築していた 772 回の貢献](docs/images/github-2013.png)

同じ人間。違う時代。違いはツールです。

**gstack が私のやり方です。** これは Claude Code を仮想エンジニアリングチームに変えます — プロダクトを再考する CEO、アーキテクチャを固定するエンジニアリングマネージャー、AI の粗悪品を見つけるデザイナー、本番バグを見つけるレビュアー、実際のブラウザを開く QA リード、OWASP + STRIDE 監査を実行するセキュリティオフィサー、そして PR を届けるリリースエンジニア。20 人の専門家と 8 つの強力なツール、すべてスラッシュコマンド、すべて Markdown、すべて無料、MIT ライセンス。

これは私のオープンソースソフトウェアファクトリーです。私は毎日それを使っています。私がそれを共有するのは、これらのツールが誰でも利用可能であるべきだからです。

フォークしてください。改善してください。あなた自身のものにしてください。そして、無料のオープンソースソフトウェアを批判したいなら — どうぞ、でもまずは試してみてください。

**誰のためのもの：**
- **創業者と CEO** — 特にまだプロダクトを届けたい技術系創業者
- **Claude Code 初心者** — 空白のプロンプトではなく構造化された役割
- **テックリードとスタッフエンジニア** — すべての PR での厳格なレビュー、QA、リリース自動化

## クイックスタート

1. gstack をインストール（30 秒 — 下記参照）
2. `/office-hours` を実行 — 何を作っているか説明
3. 機能アイデアで `/plan-ceo-review` を実行
4. 変更のあるブランチで `/review` を実行
5. ステージング URL で `/qa` を実行
6. そこで停止。これがあなたに合うか分かるでしょう。

## インストール — 30 秒

**要件：** [Claude Code](https://docs.anthropic.com/en/docs/claude-code)、[Git](https://git-scm.com/)、[Bun](https://bun.sh/) v1.0+、[Node.js](https://nodejs.org/)（Windows のみ）

### ステップ 1: マシンにインストール

Claude Code を開いてこれを貼り付け。Claude が残りをやります。

> gstack をインストール：**`git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** を実行し、CLAUDE.md に「gstack」セクションを追加。すべてのウェブブラウジングに gstack の /browse スキルを使用し、mcp__claude-in-chrome__* ツールは使用しないこと、利用可能なスキル：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、/design-consultation、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、/investigate、/document-release、/codex、/cso、/autoplan、/careful、/freeze、/guard、/unfreeze、/gstack-upgrade を記載。その後、ユーザーにチームメイトも利用できるように現在のプロジェクトに gstack を追加したいか確認。

### ステップ 2: チームメイトのためにリポジトリに追加（オプション）

> このプロジェクトに gstack を追加：**`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`** を実行し、プロジェクトの CLAUDE.md に「gstack」セクションを追加。すべてのウェブブラウジングに gstack の /browse スキルを使用し、mcp__claude-in-chrome__* ツールは使用しないこと、利用可能なスキル：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、/design-consultation、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、/investigate、/document-release、/codex、/cso、/careful、/freeze、/guard、/unfreeze、/gstack-upgrade を記載。gstack スキルが動作しない場合は `cd .claude/skills/gstack && ./setup` を実行してバイナリをビルドしスキルを登録するよう Claude に指示。

実際のファイルはリポジトリにコミットされます（サブモジュールではない）ので、`git clone` はそのまま動作します。すべては `.claude/` 内にあります。PATH に触れたりバックグラウンドで実行されるものはありません。

### Codex、Gemini CLI または Cursor

gstack は [SKILL.md 標準](https://github.com/anthropics/claude-code) をサポートするすべてのエージェントで動作します。スキルは `.agents/skills/` にあり、自動的に検出されます。

```bash
git clone https://github.com/garrytan/gstack.git ~/.codex/skills/gstack
cd ~/.codex/skills/gstack && ./setup --host codex
```

または setup にインストールされているエージェントを自動検出させます：

```bash
git clone https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

これは利用可能なものに応じて `~/.claude/skills/gstack` および/または `~/.codex/skills/gstack` にインストールされます。28 個のスキルすべてがサポートされているすべてのエージェントで動作します。フックベースのセキュリティスキル（careful、freeze、guard）は、Claude 以外のホストではインラインセキュリティアドバイザリープロースを使用します。

## 動作を確認

```
あなた：カレンダー用のデイリーブリーフィングアプリを作りたい。
あなた：/office-hours
Claude: [痛みについて質問 — 具体的な例、仮定ではない]

あなた：複数の Google カレンダー、古い情報のイベント、
        間違った場所。準備に永遠にかかり、結果は
        十分良くない...

Claude: フレーミングに異議を唱えます。「デイリー
        ブリーフィングアプリ」と言いました。しかし、
        実際に説明したのは個人の AI 参謀です。
        [あなたが説明していることに気づいていない 5 つの能力を抽出]
        [4 つの前提に挑戦 — 同意、不同意、または調整]
        [工数見積もり付きの 3 つの実装アプローチを生成]
        推奨：明日最も狭いウェッジを届け、実際の使用から
        学ぶ。完全なビジョンは 3 ヶ月のプロジェクト —
        実際に機能するデイリーブリーフィングから始める。
        [設計文書を作成 → 下流スキルに自動供給]

あなた：/plan-ceo-review
        [設計文書を読み、スコープに挑戦、10 セクションレビューを実行]

あなた：/plan-eng-review
        [データフロー、ステートマシン、エラーパスの ASCII 図]
        [テストマトリックス、失敗モード、セキュリティ懸念]

あなた：計画を承認。計画モードを終了。
        [11 ファイルに 2,400 行を記述。約 8 分。]

あなた：/review
        [自動修正] 2 問題。[質問] 競合状態 → 修正を承認。

あなた：/qa https://staging.myapp.com
        [実際のブラウザを開き、フローをクリック、バグを発見修正]

あなた：/ship
        テスト：42 → 51 (+9 新規)。PR: github.com/you/app/pull/42
```

あなたは「デイリーブリーフィングアプリ」と言いました。エージェントは「あなたは AI 参謀を構築しています」と言いました — それはあなたの機能リクエストではなく、あなたの痛みに耳を傾けたからです。8 つのコマンド、エンドツーエンド。これはコパイロットではありません。これはチームです。

## スプリント

gstack はプロセスであり、ツールのコレクションではありません。スキルはスプリントが実行される順序で実行されます：

**考える → 計画 → 構築 → レビュー → テスト → 配信 → 振り返り**

各スキルは次に供給します。`/office-hours` は `/plan-ceo-review` が読む設計文書を書きます。`/plan-eng-review` は `/qa` が受け取るテスト計画を書きます。`/review` は `/ship` が修正を検証するバグを捕まえます。すべてのステップが前のステップを知っているので、何も見逃しません。

| スキル | あなたの専門家 | 彼らは何をするか |
|-------|----------------|--------------|
| `/office-hours` | **YC オフィスアワー** | ここから始める。コードを書く前にプロダクトを再構築する 6 つの必須質問。あなたのフレーミングに異議を唱え、前提に挑戦し、実装の代替案を生成。設計文書はすべての下流スキルに供給。 |
| `/plan-ceo-review` | **CEO / 創業者** | 問題を再考。リクエストの中に隠れた 10 スタープロダクトを見つける。4 つのモード：拡張、選択的拡張、スコープ維持、縮小。 |
| `/plan-eng-review` | **エンジニアリングマネージャー** | アーキテクチャ、データフロー、図、エッジケース、テストを固定。隠れた仮定を表面に強制。 |
| `/plan-design-review` | **シニアデザイナー** | 各デザイン次元を 0-10 で評価、10 がどのようなものか説明し、そこに到達するために計画を編集。AI 粗悪品検出。インタラクティブ — デザイン選択ごとに 1 つの AskUserQuestion。 |
| `/design-consultation` | **デザインパートナー** | ゼロから完全なデザインシステムを構築。景観を調査し、創造的リスクを提案し、現実的なプロダクトモックアップを生成。 |
| `/review` | **スタッフエンジニア** | CI を通過するが本番で爆発するバグを見つける。明白なものを自動修正。完全性のギャップをフラグ。 |
| `/investigate` | **デバッガー** | 体系的な根本原因デバッグ。鉄の法則：調査なしに修正なし。データフローを追跡し、仮説をテストし、3 回の失敗した修正後に停止。 |
| `/design-review` | **コードを書くデザイナー** | /plan-design-review と同じ監査、その後見つかったものを修正。アトミックコミット、前後のスクリーンショット。 |
| `/qa` | **QA リード** | アプリをテストし、バグを見つけ、アトミックコミットで修正し、再検証。すべての修正に回帰テストを自動生成。 |
| `/qa-only` | **QA レポーター** | /qa と同じ手法だがレポートのみ。コード変更なしの純粋なバグレポート。 |
| `/cso` | **最高セキュリティ責任者** | OWASP Top 10 + STRIDE 脅威モデル。ゼロノイズ：17 の誤報除外、8/10+ 信頼度ゲート、独立した発見検証。各発見には具体的な悪用シナリオを含む。 |
| `/ship` | **リリースエンジニア** | main を同期、テストを実行、カバレッジを監査、プッシュ、PR を開く。テストフレームワークがない場合はブートストラップ。 |
| `/land-and-deploy` | **リリースエンジニア** | PR をマージ、CI とデプロイを待ち、本番の健全性を検証。「承認済み」から「本番検証済み」まで 1 コマンド。 |
| `/canary` | **SRE** | デプロイ後監視ループ。コンソールエラー、パフォーマンス回帰、ページ失敗を監視。 |
| `/benchmark` | **パフォーマンスエンジニア** | ページロード時間、Core Web Vitals、リソースサイズのベースライン。すべての PR で前後を比較。 |
| `/document-release` | **テクニカルライター** | ちょうど配信したものに合うようにすべてのプロジェクトドキュメントを更新。古い README を自動検出。 |
| `/retro` | **エンジニアリングマネージャー** | チーム認識週次振り返り。個人別内訳、配信ストリーク、テスト健全性トレンド、成長機会。`/retro global` はすべてのプロジェクトと AI ツール（Claude Code、Codex、Gemini）で実行。 |
| `/browse` | **QA エンジニア** | 実際の Chromium ブラウザ、実際のクリック、実際のスクリーンショット。コマンドあたり約 100ms。 |
| `/setup-browser-cookies` | **セッションマネージャー** | 実際のブラウザ（Chrome、Arc、Brave、Edge）からクッキーをヘッドレスセッションにインポート。認証ページをテスト。 |
| `/autoplan` | **レビューパイプライン** | 1 コマンド、完全にレビューされた計画。CEO → デザイン → エンジニアリングレビューを自動実行、エンコードされた決定原則。承認のための好みの決定のみを表面化。 |

### パワーツール

| スキル | それは何をするか |
|-------|-------------|
| `/codex` | **セカンドオピニオン** — OpenAI Codex CLI からの独立コードレビュー。3 つのモード：レビュー（合格/不合格ゲート）、敵対的挑戦、オープンコンサルテーション。`/review` と `/codex` の両方が実行されたときにクロスモデル分析。 |
| `/careful` | **セキュリティガードレール** — 破壊的コマンド（rm -rf、DROP TABLE、フォースプッシュ）の前に警告。「be careful」と言ってアクティブ化。任意の警告をオーバーライド。 |
| `/freeze` | **編集ロック** — ファイル編集を 1 ディレクトリに制限。デバッグ中のスコープ外の偶然の変更を防止。 |
| `/guard` | **完全セキュリティ** — 1 コマンドで `/careful` + `/freeze`。本番作業の最大セキュリティ。 |
| `/unfreeze` | **ロック解除** — `/freeze` 境界を削除。 |
| `/setup-deploy` | **デプロイコンフィグレーター** — `/land-and-deploy` のワンタイムセットアップ。プラットフォーム、本番 URL、デプロイコマンドを検出。 |
| `/gstack-upgrade` | **セルフアップデーター** — gstack を最新にアップグレード。グローバルとベンダードインストールを検出し、両方を同期、変更内容を表示。 |

**[各スキルの例と哲学の深い掘り下げ →](docs/skills.md)**

## 並列スプリント

gstack は 1 つのスプリントでうまく機能します。10 個が同時に実行されると面白くなります。

[Conductor](https://conductor.build) は複数の Claude Code セッションを並列実行します — それぞれが独自の隔離されたワークスペース。`/office-hours` のセッション、`/review` のセッション、機能を実装する 3 つ目のセッション、`/qa` を実行する 4 つ目のセッション。すべて同時に。スプリント構造が並列処理を機能させるものです — プロセスがなければ、10 人のエージェントは 10 の混沌の源です。プロセスがあれば、各エージェントは正確に何をすべきか、いつ停止すべきかを知っています。

---

無料、MIT ライセンス、オープンソース。プレミアムティアなし、待機リストなし。

私がソフトウェアを構築する方法をオープンソースにしました。フォークしてあなた自身のものにできます。

> **採用中。** 1 日 10K+ LOC を配信して gstack の強化を手伝いたいですか？
> YC で働く — [ycombinator.com/software](https://ycombinator.com/software)
> 非常に競争力のある給与と株式。サンフランシスコ、Dogpatch 地区。

## ドキュメント

| ドキュメント | カバー内容 |
|-----|---------------|
| [スキル深い掘り下げ](docs/skills.md) | 各スキルの哲学、例、ワークフロー（Greptile 統合を含む） |
| [ビルダーの精神](ETHOS.md) | ビルダー哲学：湖を沸騰させる、構築前に検索、3 層の知識 |
| [アーキテクチャ](ARCHITECTURE.md) | デザイン決定とシステム内部 |
| [ブラウザリファレンス](BROWSER.md) | `/browse` の完全コマンドリファレンス |
| [コントリビューション](CONTRIBUTING.md) | 開発セットアップ、テスト、コントリビューターモード、開発モード |
| [チェンジログ](CHANGELOG.md) | すべてのバージョンの新機能 |

## プライバシーとテレメトリ

gstack にはプロジェクトの改善を支援する**オプトイン**の使用テレメトリが含まれています。正確には次のようになります：

- **デフォルトはオフ。** 明示的に「はい」と言わない限り、何も送信されません。
- **初回実行時、** gstack は匿名使用データを共有したいか確認。いいえと言えます。
- **送信されるもの（オプトインした場合）：** スキル名、期間、成功/失敗、gstack バージョン、OS。それだけ。
- **決して送信されないもの：** コード、ファイルパス、リポジトリ名、ブランチ名、プロンプト、またはユーザー生成コンテンツ。
- **いつでも変更可能：** `gstack-config set telemetry off` ですべてを即座に無効化。

データは [Supabase](https://supabase.com)（オープンソース Firebase 代替）に保存。スキーマは [`supabase/migrations/001_telemetry.sql`](supabase/migrations/001_telemetry.sql) — 何が収集されるか正確に確認できます。リポジトリの Supabase パブリッシュキーは公開キー（Firebase API キーのようなもの） — 行レベルセキュリティポリシーにより挿入のみに制限。

**ローカル分析は常に利用可能。** `gstack-analytics` を実行してローカル JSONL ファイルから個人使用ダッシュボードを表示 — リモートデータ不要。

## トラブルシューティング

**スキルが表示されない？** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` が失敗？** `cd ~/.claude/skills/gstack && bun install && bun run build`

**インストールが古い？** `/gstack-upgrade` を実行 — または `~/.gstack/config.yaml` で `auto_upgrade: true` を設定。

**Windows ユーザー：** gstack は Git Bash または WSL を介して Windows 11 で動作。Bun に加えて Node.js が必要 — Bun には Windows 上の Playwright のパイプトランスポートに既知のバグがあります（[bun#4253](https://github.com/oven-sh/bun/issues/4253)）。ブラウズサーバーは自動的に Node.js にフォールバック。`bun` と `node` の両方が PATH にあることを確認。

**Claude がスキルを見られないと言う？** プロジェクトの `CLAUDE.md` に gstack セクションがあることを確認。これを追加：

```
## gstack
すべてのウェブブラウジングに gstack の /browse を使用。mcp__claude-in-chrome__* ツールは使用しない。
利用可能なスキル：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、
/design-consultation、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、
/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、
/investigate、/document-release、/codex、/cso、/autoplan、/careful、/freeze、/guard、
/unfreeze、/gstack-upgrade。
```

## ライセンス

MIT。永遠に無料。何かを構築しに行こう。