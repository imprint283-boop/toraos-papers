# 寅OS：論文4本と普遍意味憲法

**非公開の公開準備版／2026-09-30。公開、リリース、DOI取得は行っていません。**

主体ごとに文脈・判断・権限を保持し、必要な関係を通じて接続し、現実の結果から次の行動を更新するという寅OSの考え方をまとめた文書集です。論文は査読なしの提案・研究段階です。研究仮説、将来像、過去の部分実装報告を、実証済みの能力や現在の実装状況として読むことはできません。実装コードは含みません。

| 文書 | 原文の時点・版 | 内容 |
|---|---|---|
| P0 | 2026-08-29／v0.1 | 主体中心型・進化型AI OSの本体提案と、当時の部分実装報告 |
| P1 | 著者・執筆日未確定／v1.0 | 任意Subject、複数View、方向付きRelation等の概念ノート |
| P2 | 2026-09-19／v0.1 | LLM意味地図、外部知性補完、関係知性の研究仮説 |
| P3 | 2026-09-28／v0.1 | 複数PersonalとCommunityの相互視点 |
| 憲法 | Rev006／revision識別子の基準日2026-08-12 | 普遍意味文法。本文には別の執筆日・公開日の記載なし |

P1のGoogle文書の作成記録は2026-08-30です。これは執筆日・公開日の確定ではありません。P3は2026-09-28に後から著者採用されていますが、作成時の本文にある確認待ち等の記載は歴史資料としてそのまま残しています。

日本語の原文は1文字も変更していません。**日本語が正、英訳は下書き**です。意味に相違があれば日本語を優先します。P0〜P3の英訳は既存A7案を使用し、憲法の英訳は2026-09-30に作成しました。本文の修正は原文の上書きではなく、注記または新しい版として扱います。

P2の日本語原文は非公開資料の位置情報を含むため、ファイル全体をこの公開候補から除外しています。原文は変更せず非公開の準備資料に保存済みで、英訳は収録しています。P0の非公開実装リポジトリへの言及、著者の経歴、P1の動物名の例は本人の公開判断待ちです。この版のまま公開する許可はありません。

個々の文書、原文・英訳へのリンク、引用案は [PAPERS.md](PAPERS.md) にあります。非公開の対話、実装リポジトリ、内部資料は同梱しておらず、それらに依存する説明を第三者がこの文書集だけで独立検証できるとは主張しません。

## AI利用

P0はChatGPTによる設計対話、Codexによる実装・試験・修正の補助を本文で説明しています。P2・P3は著者との対話を起点に生成AIが文献確認、整理、執筆を補助したことを明記しています。P0・P1・憲法の過去の原稿作成に使ったAIや文章生成補助の詳しい範囲は確定していません。既存英訳はA7由来のAI補助による下書きで、本準備ではCodexが文書の組立て、憲法英訳、案内・引用・Zenodo情報の下書きを行いました。P0・P1を含む日本語本文は今回AIが書き換えていません。AIの生成物や内部点検は査読や実証の代わりではありません。

## 引用と公開情報

個別論文の引用はPAPERS.mdを参照してください。CITATION.cffは文書集用の引用下書きで、表示には`preferred-citation`の`generic`を使います。CFFのroot `type`はsoftware/datasetしか選べず、省略時の既定はsoftwareという仕様上の制約があります。この文書集ではroot `type`を省略し、文書集の引用は`preferred-citation`で明示しています。ソフトウェアリリースの引用情報を転用していません。P1の著者・日付、ライセンス、公開日、リリース版、DOI、ORCIDは未確定の値を補っていません。

ライセンス：

ライセンスは翼さんの決定待ちです。ライセンス文書や利用許諾は有効化していません。公開判断と必要な情報の確定まで非公開のままにします。

Zenodo用の情報案は [zenodo/metadata.candidate.json](zenodo/metadata.candidate.json) にあります。自動取り込み用のroot `.zenodo.json` は設置していません。ライセンスの空欄は有効な公開設定ではなく、公開許可と確定後に正式な情報へ転記するための準備ファイルです。

## English

This private preparation set contains four ToraOS research papers and the Universal Semantic Constitution, Rev006. The papers are proposals and research drafts, not peer-reviewed publications. Historical implementation reports, research hypotheses, and predictions are distinct from current implementation evidence. Japanese originals are authoritative; English versions are translation drafts. The P2 Japanese original is withheld in its entirety because it contains private source locators; it has been preserved unchanged outside the publication candidate. P1 authorship and original date, the license, and personal-disclosure decisions remain unresolved. No public release or DOI has been created.
