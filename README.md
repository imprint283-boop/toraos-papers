# 寅OS：論文4本と普遍意味憲法

**非公開の公開準備版／2026-09-30。公開、リリース、DOI取得は行っていません。**

主体ごとに文脈・判断・権限を保持し、必要な関係を通じて接続し、現実の結果から次の行動を更新するという寅OSの考え方をまとめた文書集です。論文は査読なしの提案・研究段階です。研究仮説、将来像、過去の部分実装報告を、実証済みの能力や現在の実装状況として読むことはできません。実装コードは含みません。

| 文書 | 原文の時点・版 | 内容 |
|---|---|---|
| P0 | 2026-08-29／v0.1 | 主体中心型・進化型AI OSの本体提案と、当時の部分実装報告 |
| P1 | 2026-08-30／v1.0（著者：中川 翼） | 任意Subject、複数View、方向付きRelation等の概念ノート |
| P2 | 2026-09-19／v0.1 | LLM意味地図、外部知性補完、関係知性の研究仮説 |
| P3 | 2026-09-28／v0.1 | 複数PersonalとCommunityの相互視点 |
| 憲法 | Rev006／revision識別子の基準日2026-08-12 | 普遍意味文法。本文には別の執筆日・公開日の記載なし |

P1の著者は中川 翼、日付は2026-08-30と、2026-09-30に本人が確定しました。Google文書の作成記録も2026-08-30ですが、今回の引用情報は本人の決定を根拠としています。文書集の公開日は別で、まだ設定していません。P3は2026-09-28に後から著者採用されていますが、作成時の本文にある確認待ち等の記載は歴史資料としてそのまま残しています。

保存している日本語の元原本は1文字も変更していません。P2には、本人の指定により非公開Driveリンク2箇所だけを伏せ、冒頭に説明を付けた別の公開版を収録しています。**日本語が正、英訳は下書き**です。意味に相違があれば日本語を優先します。P0〜P3の英訳は既存A7案を使用し、憲法の英訳は2026-09-30に作成しました。本文の修正は原文の上書きではなく、注記または新しい版として扱います。

P2の元原本は変更せず非公開の準備資料に保存済みで、公開候補には上記の日本語公開版と英訳を収録しています。P0の非公開実装リポジトリへの言及と著者の経歴、P1のピノの例は、そのまま出してよいと本人が確認しました。ピノは翼さんの猫です。これらの決定と、リポジトリを実際に公開する許可は別です。翼さんの「出す」の指示まで非公開のままにします。

個々の文書、原文・英訳へのリンク、引用案は [PAPERS.md](PAPERS.md) にあります。非公開の対話、実装リポジトリ、内部資料は同梱しておらず、それらに依存する説明を第三者がこの文書集だけで独立検証できるとは主張しません。

## AI利用

論文4本の発案・考え方は中川 翼、文章化・本文執筆はGPTによるものです。これは2026-09-30の本人の申告に基づく開示です。著者名は本人が中川 翼と指定しています。原稿を書いたGPTの詳細なモデルID・具体的な作業日時は未確認です。

P0本文のChatGPTによる設計対話・Codexによる実装等の説明、P2・P3本文の生成AIによる執筆補助の記載は、作成時の記録としてそのまま残しています。憲法の元原稿については、過去の作成モデルや文章生成の範囲は未確認であり、上記の論文に関する申告を憲法に広げていません。

既存英訳はA7由来のAI補助による下書きで、本準備ではCodexが文書の組立て、憲法英訳、案内・引用・Zenodo情報の下書きを行いました。保存する日本語の元原本は今回AIが書き換えていません。P2の公開用別版だけは、本人の指定した2リンクを伏せて冒頭注記を付けました。AIの生成物や内部点検は査読や実証の代わりではありません。

## 引用と公開情報

個別論文の引用はPAPERS.mdを参照してください。CITATION.cffは文書集用の引用情報で、表示には`preferred-citation`の`generic`を使います。CFFのroot `type`はsoftware/datasetしか選べず、省略時の既定はsoftwareという仕様上の制約があります。この文書集ではroot `type`を省略し、文書集の引用は`preferred-citation`で明示しています。ソフトウェアリリースの引用情報を転用していません。P1の著者・日付と文章のライセンスは本人が確定しました。公開日、リリース版、DOI、ORCIDは未確定の値を補っていません。

ライセンス：[CC BY 4.0](LICENSE)（Creative Commons Attribution 4.0 International）。

論文4本と憲法の文章は、本人の決定によりCC BY 4.0を適用します。作者を適切に表示し、変更を明示する条件で利用・改変・再配布できるライセンスです。他者の引用部分や、このライセンスが扱わない権利まで新しく許諾するものではありません。リポジトリの公開、リリース、Zenodo操作はまだ行っていません。

Zenodo用の情報はroot [.zenodo.json](.zenodo.json) に用意しました。[zenodo/metadata.candidate.json](zenodo/metadata.candidate.json) は同じ内容の確認用コピーです。文章のライセンスは`cc-by-4.0`を明記しています。ファイルの用意だけで登録・公開されることはありません。公開日・公開版・DOIは実際の公開時に確定します。

## English

This private preparation set contains four ToraOS research papers and the Universal Semantic Constitution, Rev006. The papers are proposals and research drafts, not peer-reviewed publications. Historical implementation reports, research hypotheses, and predictions are distinct from current implementation evidence. Japanese originals are authoritative; English versions are translation drafts. P2 is included as a separate Japanese publication version with only two private Drive links masked and an explanatory notice added; its source original is preserved unchanged in private material. On 2026-09-30, the author confirmed P1 authorship as Tsubasa Nakagawa and its date as 2026-08-30, approved the identified personal disclosures, and selected CC BY 4.0 for the texts. The repository remains private until explicit publication authorization. No public release or DOI has been created.
