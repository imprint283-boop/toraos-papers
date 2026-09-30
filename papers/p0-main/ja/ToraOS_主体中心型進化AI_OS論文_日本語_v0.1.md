# ToraOS：主体中心型・進化型AI OSアーキテクチャの提案
## 独立した文脈・権限、方向付き関係、実結果駆動の継続成長

**中川 翼**  
独立研究・実践開発  
草稿 v0.1 / 2026年8月29日

> **論文種別**：ポジションペーパー兼アーキテクチャ提案・部分的リファレンス実装報告  
> **注記**：本稿は査読前草稿である。ToraOSの現行実装、将来構想、著者の研究仮説、社会的未来予想を明示的に分離する。ToraOSが「世界初」であること、世界規模で成立すること、社会的に望ましいことを本稿は主張しない。

## 要旨

生成AIを長期間利用すると、単発の会話性能とは異なる問題が現れる。過去の判断が次の作業へ反映されない、人物・組織・案件の文脈が混ざる、何を事実とみなしたかの根拠が失われる、AIの提案が採用されたことと実際に有効だったことが混同される、といった問題である。本稿は、これらを単なる「長期記憶」の不足ではなく、AIシステムの基本単位の置き方に起因する問題として捉える。

本稿では、**主体中心型・進化型AI OS**というアーキテクチャを提案する。同一のOS核を、人、会社、家族、コミュニティ、プロジェクト等の異なる「主体」ごとに独立して成立させ、各主体が固有の原情報、意味解釈、文脈、判断、実結果、権限を保持する。主体間で文脈そのものを暗黙に統合せず、出典・方向・時点・有効範囲・権限・開示条件を持つ**方向付き関係**を介して接続する。反対方向の関係が独立に成立し、双方が同一の現実関係を指すと確認できた場合には相互関係を投影できるが、元の二つの主張は保持する。この相互性は、資格、所属、保証、委任、権威、信用等の「関係価値」を形成し得る。ただし、それを単一の社会信用スコアへ集約しない。

ToraOSはこの構想の部分的リファレンス実装である。2026年8月29日時点の私有リポジトリでは、原情報と派生情報の分離、フィールド単位の権威管理、出典で拘束された共有状態、文脈推論、関係候補の検証・審査・受理、実作業への文脈適用、成果物と所有者判断・実利用の分離、実結果からの修正、再発時の選択改善に向けた経路が実装されている。一方、複数の独立ToraOS主体間の連合、相互関係プロトコル、公開適合仕様、社会的信用交換は未実装であり研究仮説である。

本稿の主な貢献は、(1) AIの記憶を利用者アカウントの付属物ではなく主体自身の状態として扱う抽象化、(2) 主体ごとの文脈・権限を混ぜずに接続する関係境界、(3) 一方向主張と相互確認を分離した関係モデル、(4) 記憶量ではなく将来行動の改善を成長条件とする実結果駆動ループ、(5) これらを実コード、権限文書、開発履歴と結び付けた検証可能な公開研究計画、の五点である。

**キーワード**：主体中心型AI、長期文脈、権限分離、方向付き関係、相互関係、来歴、継続学習、分散AI、オープンソース

---

# 1. はじめに

大規模言語モデルの性能向上により、AIは検索や文章生成だけでなく、計画、コーディング、資料作成、業務支援、意思決定支援へ広がった。しかし、利用期間が数か月、数年に伸びると、単純な「モデル性能」では説明しにくい問題が現れる。

第一に、**記憶されていることと、次の判断へ有効に使われることは別である**。大量の履歴を保存しても、現在の目的と関係する過去だけを選べなければ、むしろ雑音が増える。第二に、**同じ人物や組織について、異なる主体が異なる認識を持つことは正常である**。個人の私的判断と会社の公式判断を一つの巨大な知識グラフへ統合すると、出典、責任、秘密保持、時点、正当な決定権が崩れる。第三に、**AIが作った成果物が受け入れられたことと、その成果物が現実で有効だったことは異なる**。納品、採用、利用、結果、修正を一つの成功状態へ潰すと、AIは「何が効いたのか」を学べない。

ToraOSは、この問題を一人の利用者の長期AI利用から出発して実装してきたシステムである。現行の普遍意味憲法では、原情報、証拠、記録、主張、推論、現在像を区別し、世界共通の唯一の真実や全主体を統治する単一目標を置かないことが明記されている。また、会社や組織化されたコミュニティが独立主体になり得る一方、緩いコミュニティや地域、世界は必ずしも一つの巨大主体にしないという境界を持つ。[内1]

本稿は、この実装と設計を一段抽象化し、次の問いを扱う。

- **研究問い1**：人、会社、コミュニティ等を別製品に分けず、同一のOS核を異なる主体へ成立させられるか。
- **研究問い2**：主体ごとの文脈と権限を暗黙に混ぜず、それでも社会的な関係を表現できるか。
- **研究問い3**：一方向の関係主張と相互確認を分離することで、中央の単一信用スコアに依存しない信用・保証・権威の表現が可能か。
- **研究問い4**：単なる長期記憶ではなく、実結果と修正を次の初回行動へ戻すことを「成長」と定義できるか。
- **研究問い5**：この構造を特定製品に閉じず、別実装やフォークが参加できる公開アーキテクチャへ発展させられるか。

本稿はこれらに対する完成済みの実証結果を示すものではない。現在成立している部分、コードで確認できる部分、著者が採用した方向、未検証の研究仮説、社会的未来予想を分け、その境界自体を研究成果の一部として提示する。

# 2. 研究・開発の起点と方法

## 2.1 非専門家による実践駆動型の出発

著者は2026年時点で46歳であり、ソフトウェア開発を専門教育や職業として経験してこなかった異業種の実務者である。生成AIを本格的に触り始めたのはおおむね2025年頃で、2026年5月頃からコード実装へ進み、同年6月以降は利用枠の大きい有料プランへ移行してToraOSの開発を本格化した。周囲に日常的に相談できるプログラマーや高度なAI利用者がいない環境で、設計上の壁打ちは主としてChatGPT、実装・試験・修正は主としてCodexとの対話を通じて行った。

2026年5月27日の開発記録では、当初のToraOSは「本人の判断履歴によって育つ個人用AI基盤」として整理され、最小成功条件は「成果物 → 本人評価 → 判断基準抽出 → 次回反映」の一循環とされた。[内2] 当時はObsidianを記憶庫として使う案、部門型AI、評価ログ、一時AI等、現在とは異なる物理構造を多数検討していた。重要なのは、その後に箱や製品名が何度も入れ替わった一方、**本人の判断・違和感・修正・実結果を次回へ生かす**という目的が残ったことである。

この経歴は、アーキテクチャの新規性や正しさを証明するものではない。ただし、既存の分散システムや知識表現の教科書的分類からトップダウンに設計したのではなく、長期利用で生じた失敗を一つずつ分解する中で、原情報、意味解釈、文脈、権限、関係、実結果の分離へ到達したという形成過程を理解する上で重要である。

## 2.2 研究材料

本稿は、次の五種類の一次資料を突合して作成した。

1. **現行権限文書**：普遍意味憲法、個人Tora憲法・プロフィール、現行運用方針、Harness方針、Current Authority Registry。
2. **採用済み要件定義**：ToraOS要求・要件定義 v1.2、判断・成長・データ設計、システム構成・連携・権限設計等。
3. **ToraOS OPEN将来候補**：v0.3統合版、追加深掘り意味契約、Gap監査、公開Gate等。これらは現行実装権限を持たない非正本候補として読む。
4. **実装コード**：2026年8月29日時点の私有GitHubリポジトリ `imprint283-boop/toraos-shadow-harness` のmain、commit `3c4ccac069034b75f776b0b0109b9964f5003a5a` を実装上の基準とした。[内3]
5. **開発Trajectory**：2026年5月以降の設計対話、要件改訂、失敗、監査、PR、Canary、Owner修正。

本稿では、要件文書の存在だけを「実装済み」とみなさず、コードの存在だけを「実運用価値が証明された」ともみなさない。

## 2.3 主張の階層

混同を避けるため、本稿では主張を次の五階層に分ける。

| 階層 | 意味 | 例 |
|---|---|---|
| A：現行権限 | 現在の正本・権限文書で有効な意味 | 世界共通Truthを置かない、別主体へPersonal Goalを強制しない |
| B：実装証拠 | mainコード・試験・受理済みReceiptで確認できる機構 | Authority Map、関係受理台帳、Outcome/Correction経路 |
| C：著者方向 | 著者が現在の構想として明示している方向 | 同一OSをSubjectごとに独立成立させる |
| D：研究仮説 | 実証前の技術・社会仮説 | 相互Relationが文脈依存の信用資産になる |
| E：未来予想 | 社会制度・市場まで含む長期予想 | SaaS/SNSが主体中心のAdapterへ相対化される |

この階層は、完成品に見せるための説明上の逃げ道ではなく、反証可能性を維持するための研究上の境界である。

# 3. 関連研究と既存技術

ToraOSの各要素には明確な先行技術が存在する。したがって本稿は「AIに長期記憶を持たせた」「関係グラフを使った」「分散IDを使う」という個別要素を新規性として主張しない。

## 3.1 分散個人データ基盤とSolid

Solidは、利用者データをアプリケーションから分離し、個人オンラインデータストアであるPodに保持し、アプリが権限の範囲でデータを利用する分散Web基盤である。[1][2] SolidのWebIDは人だけでなく組織等の主体も指し得る。現行Solid ProtocolでもWebIDはperson、organisation、software等のagentを指すとされている。[2]

この点はToraOSの「サービスがデータを囲い込むのではなく、主体側が状態を持つ」という思想に近い。一方、Solidの中心課題はデータの所有、アクセス、相互運用であり、主体ごとのAI判断、実結果、修正、将来行動の改善を一つのOSループとして定義するものではない。また、Solid上で生成AIを利用するSocialGenPodのような研究は、私有データと生成AIの分離・移植性を示しているが、主体単位の権限・判断・Outcome成長までは扱わない。[10]

## 3.2 分散識別子と検証可能資格

W3Cの分散識別子（DID）は、人、組織、物、データモデル、抽象的対象等の「任意のsubject」を参照でき、中央のIDプロバイダから識別を分離する。[4] 検証可能資格情報（Verifiable Credentials）は、発行者、保有者、検証者の関係で、学歴、免許、資格等の主張を暗号的に検証可能な形で交換する。[5] また資格の失効・停止を扱う標準も存在する。[6]

これらはToraOSが将来扱う「誰が誰について何を保証したか」「その主張は現在有効か」という関係価値の重要な基盤候補である。しかし、DID/VC自体は主体の長期文脈、意思決定、実結果、AIによる継続成長を定義しない。ToraOSはこれらを再発明するべきではなく、将来の公開プロトコルでは既存標準を利用・接続する側に立つべきである。

## 3.3 分散SNSとActivityPub

ActivityPubは分散SNSのための標準であり、異なる実装のサーバ間でActorがコンテンツや通知を交換できる。[3] 「中央SNSに全員が集まらなくても社会的ネットワークが成立する」という点で、ToraOSの将来像と共通する。

しかしActivityPubのActorは主に社会的メッセージ交換の主体であり、主体内部の原情報・権限・判断・実結果・修正を独立した認知OSとして保持することは目的ではない。ToraOSの将来連合はActivityPubと競合するより、必要なら社会的配送経路の一つとして利用できる方が自然である。

## 3.4 来歴とPROV

W3C PROVは、Entity、Activity、Agentと、それらの生成・派生・責任関係を用いて、異なるシステム間で来歴情報を交換する標準を提供する。[7] ToraOSが重視する「何が原情報で、誰が観測し、何から派生し、誰がどの権限で判断したか」という考え方は、来歴研究の長い蓄積と接続できる。

ToraOSの独自性を「来歴を持つこと」に置くべきではない。むしろ既存の来歴原則を、AIの文脈選択、関係候補、判断、成果物、実利用、修正という長期成長ループへ適用する点に意味がある。

## 3.5 LLMエージェントの長期記憶と継続学習

LLMエージェントの長期記憶は既に大きな研究領域であり、記憶の書込み、保存、検索、反省、階層化、継続学習等が整理されている。[8][9] 2026年の調査では、長期記憶の安全性を、書込み、保存、検索、実行、共有・伝播、忘却・ロールバックのライフサイクルとして扱う研究も現れている。[14]

ToraOSはこの領域と重なるが、「AIエージェント自身の記憶」を最上位概念にしない。記憶は主体のSourceやContextの一部であり、AIモデルやProviderは交換可能な実行エンジンと位置付ける。現行要件でもToraはLLMそのものではなく、Event Ledger、Decision Scene、Goal Structure、Decision Model、Context Selection、Outcome Feedbackの組合せとして定義されている。[内4]

## 3.6 信用・評判・Web of Trust

ネットワーク上の関係から信用や評判を導く研究も古くから存在する。取引後評価を集約する評判システム、P2Pネットワークでの信頼グラフ、Web of Trust、グラフ中心性に基づく信用推定等が多数研究されてきた。[11][12]

したがって「Relationが信用になる」こと自体は新規ではない。本稿が提案する差は、**信用を一つのグローバル評判値へ潰すのではなく、主体ごとの独立した方向付き主張、相互確認、第三者保証、出典、権限、時間、有効範囲、実結果を保持し、必要な場面でだけ関係経路として評価する**点にある。

## 3.7 本稿の位置

既存技術を要素ごとに並べると、ToraOSは以下の交点に位置する。

| 系譜 | 既にある強み | ToraOSが追加しようとするもの |
|---|---|---|
| Solid / PDS | データ主権、アプリとデータの分離 | 主体の判断・実結果・修正を含む進化OS |
| DID / VC | 分散識別、資格・保証の検証 | 主体内部のContext/Outcomeと関係価値の接続 |
| ActivityPub | 異種実装間の社会的連合 | 文脈・権限を保持したSubject OS間連合 |
| PROV | 来歴、派生、責任 | AI文脈選択とOutcome学習への適用 |
| LLM Memory | 長期記憶、検索、反省 | AIではなくSubjectを状態の所有者にする |
| Trust/Reputation | 関係から信用を推定 | 単一Scoreを避け、相互RelationとAuthority Pathを保持 |

本稿の新規性候補は単一技術ではなく、**主体主権 + AI認知 + 権限分離 + 方向付き関係 + 実結果学習**を、同一OSの反復可能な主体単位として統合するアーキテクチャにある。

# 4. 問題設定：プラットフォーム中心から主体中心へ

現在のWebサービスの多くは、利用者がサービスごとにアカウントを持ち、プロフィール、履歴、人間関係、信用、業務記録を各サービス内部へ複製する「プラットフォーム中心型」である。

```text
サービスA ─ 利用者Aのプロフィール・履歴・関係
サービスB ─ 利用者Aのプロフィール・履歴・関係
サービスC ─ 利用者Aのプロフィール・履歴・関係
```

このモデルでは、同一人物について複数の断片が存在し、サービスを離れると関係や履歴の一部も失われる。会社についても、CRM、チャット、会計、人事、カレンダー等が会社の断片を各SaaS内部に持つ。

主体中心型では、一次単位をサービスではなく主体へ移す。

```text
                 主体A
       ┌─────────┼─────────┐
       │         │         │
    サービス1  サービス2  サービス3
      Adapter / Storage / Execution / Delivery
```

サービスは不要になるのではない。保存、決済、配送、計算、UI、法的手続等の能力を提供する。しかし、主体の長期Identity、文脈、権限、判断履歴の唯一の所有者である必要はなくなる。

この方向はSolid等と共通する。本稿がさらに要求するのは、主体内部にAIが継続的に意味を解釈し、過去の判断と実結果を将来の行動へ反映する認知ループを持つことである。

# 5. 提案アーキテクチャ

## 5.1 「一つのOS、任意の主体」

ToraOSの最新の著者方向では、Personal Tora、Company Tora、Community Toraを別製品として定義しない。

> **一つのOS核を、異なる主体について独立して成立させる。**

概念的には、各インスタンスを次のように表す。

```text
T_i = K + P_i + X_i
```

ここで、

- `K`：全主体で共通する意味・安全・来歴・関係・時間・実結果のOS核
- `P_i`：主体iの憲法、権限、能力、開示方針、役割等のプロフィール
- `X_i`：主体iに属する原情報、派生状態、判断、Outcome、履歴

である。

人、会社、家族、コミュニティ、プロジェクトは「OSの種類」ではなく**主体の種類**である。同じKernelを用いながら、必要なCapabilityだけが有効になる。会社であればGovernanceやRole、代表権が重要になり、個人では私的Goalや判断履歴が中心になり、概念SubjectであればAction能力を持たないことも正常である。この考え方はToraOS OPEN v0.3のOptional Capability思想および現行普遍意味憲法の「Subjectは複数Goal、対立Goal、Goalなしを持ち得る」という原則と整合する。[内1][内5]

## 5.2 主体と現実対象を同一視しない

ToraOS OPEN v0.3では、現実世界のEntity/ConceptとTora Subjectを分離している。[内5] この分離は必須である。

「北野同朋会という現実組織」と「北野同朋会をSubjectとして持つToraOS」は同一ではない。誰でも同名のデジタルSubject候補を作れるとしても、それだけで公式性や代表権は得られない。実世界でのRecognition、資格、役割、設立手続、代表Authority等を別Relationとして検証する必要がある。

これはDIDにおけるsubject/controller分離とも親和性が高い。ToraOSは独自の世界共通ID体系を発明するより、既存の識別・資格標準を受け入れられる意味境界を持つべきである。

## 5.3 主体ごとのContextとAuthorityを混ぜない

同じEntityが複数主体に現れても、各主体が何を知っているか、何を正とするか、何を使ってよいかは別である。

例えば、個人Subject Aと会社Subject Bの双方に「人物X」というEntityが存在しても、

- Aは私的経験、個人的予定、個人的評価を持つ
- Bは役職、雇用上の記録、会社としてのDecision、組織Outcomeを持つ

という差がある。

本稿では、主体iのContext集合を `C_i` とし、異なる主体jへ自動継承しないことを基本条件とする。

```text
i ≠ j のとき、C_i は C_j へ暗黙コピーされない。
```

境界を越えられるのは、明示的に開示されたClaim、Relation、Credential、Artifact、またはそれらへの検証可能な参照であり、開示は当該主体のAuthorityとPolicyに拘束される。

この原則は現行Personal Toraでも既に現れている。Personal作業から別SubjectのSource/Relation/Outcome候補を作れても、公式Subjectへ反映するにはそのSubjectの成立手続、Authority、Permissionが必要とされる。[内6]

## 5.4 二種類のAuthorityを分ける

ToraOSでは「Authority」という語が二つの層で使われるため、論文上は区別する。

### 5.4.1 データ権威

実装上のAuthority Mapは、あるfieldについて、どのstore、binding、writerが唯一の正本更新者かを決める。現行コードでは `canonical`、`shared_authoritative`、`local_authoritative`、`derived`、`cache` 等を分け、各fieldに正確に一つのauthoritative writerを要求し、revisionを一段ずつ進める。[内7]

これは「どのデータを正と読むか」の技術的権威である。

### 5.4.2 主体権限

一方、普遍意味憲法におけるAuthorityは、Framework、Source、成立手続、Role、Holder、Scope、Validity、Evidence、撤回・係争へ辿れるClaimである。[内1] 例えば、会社の代表取締役が契約する権限は、単なるデータベースwrite permissionではない。

本稿では前者を**データ権威**、後者を**主体権限**と呼ぶ。能力があること、システム権限があること、社会的に正当な決定権があることを混同しない。

## 5.5 Relationは方向付きStatementである

関係は無向の線ではない。

```text
A → B
```

と

```text
B → A
```

は独立した主張である。

ToraOS OPEN v0.3も「Relation is Directional Statement」を明示し、相互Relationは複数方向のStatementが整合した時にProjectionできるとしている。[内5]

本稿では一つのRelationを概念的に次の組として表す。

```text
r = (
  発行主体,
  対象,
  関係種別,
  方向,
  出典,
  権限範囲,
  時点・有効期間,
  条件,
  反証,
  開示条件,
  状態
)
```

現行ToraOSのRelation実装にも `subject_ref`、`object_ref`、`family`、`relation_type`、`direction`、Source refs、counterevidence、conditions、valid time、provenance、confidence等が存在する。[内8]

## 5.6 一方向Relationと相互Relation

例えば、個人Aが「私は会社Bの役員である」と記録したRelationは、A側の主張として価値を持つが、それだけで会社側の公式認識を意味しない。

```text
A → ROLE_CLAIM → B
```

会社B側に、適切な権限を持つ手続から

```text
B → APPOINTED → A
```

が独立に成立し、両Relationが同一の役職・期間・Scopeを指していることを検証できた場合、相互関係を投影できる。

重要なのは、相互化した後も元の二つのRelationを消さないことである。

```text
相互関係 = Projection(r_A→B, r_B→A)
```

この構造なら、

- Aは所属を主張しているがBは認めていない
- Bは所属を主張しているがAは退職済みと主張している
- 第三者機関Cが一方を保証している
- 双方は一致するが有効期間が切れている

といった現実の不一致を保持できる。

## 5.7 Relationが価値を持つ条件

本稿は、Relation数が多いほど価値が高いとは考えない。既存の評判システムが陥りやすい単一Score化を避ける。

ある関係の価値 `V` は、利用目的 `q` に依存する文脈関数として考える。

```text
V_q(r) = F(
  相互性,
  発行主体のAuthority,
  出典と来歴,
  独立した支持,
  有効期間,
  反証,
  第三者保証,
  過去Outcome
)
```

ここでFは必ずしも数値関数ではない。説明可能なEvidence Pathでもよい。

例えば「100万人にフォローされている」というRelation束と、「特定資格機関が有効な資格を発行している」というRelationは用途が違う。住宅賃貸、採用、行政、コミュニティ参加等で必要な関係経路も異なる。

本稿では、このように主体が独立したまま他主体から受け取る検証可能なRelationの束を、便宜上**検証可能な関係資本**と呼ぶ。これは新しい世界共通通貨や社会信用点を意味しない。

## 5.8 Relationの推移を自動保証しない

AとB、BとCが強く接続していても、AがCを信用するとは限らない。

```text
A ↔ B ↔ C
```

から

```text
A trusts C
```

を自動導出してはならない。

使えるのは「AとCの間に、Bを経由した検証可能な経路がある」という事実である。推移可能性はrelation type、scope、法的意味、時間、目的に依存する。現行ToraOSが相関を因果へ自動昇格しない設計と同様、関係経路を信用へ自動昇格しない。

## 5.9 SourceからOutcomeまでを分離する

ToraOSの重要な不変条件は、以下を一つの状態へ潰さないことである。

```text
原情報(Source)
  ↓
意味解釈(Semantic / Claim / Inference)
  ↓
関係(Relation)
  ↓
文脈選択(Context Selection)
  ↓
行動・成果物(Action / Delivery)
  ↓
所有者判断(Decision)
  ↓
実利用・実結果(Outcome)
  ↓
修正(Correction)
  ↓
次回のContext / Action
```

現行の自律Context/Trajectory/Outcome Growth Loop契約でも、Context数やRelation数を成功指標にせず、過去Evidenceが初回Actionを変え、後のOwner Evidenceが正確なDeliveryとContext Applicationへ結び付き、その修正が後の通常選択へ入力されたかを価値テストとしている。[内9]

「これでいい」という返答はDecisionであり、成功利用ではない。Delivery、Owner Decision、利用、Outcome、Correctionを分けることで、AIは成果物が受け入れられた理由と、現場で実際に機能した理由を区別できる。

# 6. 現行ToraOSの実装

## 6.1 2026年8月29日時点の実装基準

本稿が確認したprivate repositoryのmain HEADは `3c4ccac069034b75f776b0b0109b9964f5003a5a` である。このcommitはPR #36「Add nonactivated Codex Hook payload bridge」のmergeであり、2026年8月29日01時03分頃（日本時間）に相当する。[内3]

リポジトリREADMEは現時点を`private development history`とし、public releaseやopen-source licenseは未承認であることを明示している。[内3] したがって、本稿執筆時点で「ToraOSはOSSである」とは記載できない。OSS化は著者の現在の目標である。

## 6.2 4層Authority

Current Authority Registry revision `TOROS-CURRENT-AUTHORITY-REGISTRY-20260828-038` は次の4層をCurrentとして選択する。[内10]

1. 普遍意味憲法
2. Personal Tora Constitution / Profile
3. Current Operating Policy
4. Harness Adapter Policy

この構造により、「ToraOSとは何か」という普遍意味、「このSubjectで何を目指すか」という個別意味、「現在どう変更・運用するか」、「実行Harnessへどう投影するか」が分かれている。

これは将来のmulti-subject化に重要である。Personal ToraのGoalやAuthoritative Ownerを普遍層へ固定せず、別Subjectへ自動継承しない境界が既にCurrentに存在する。[内1][内6]

## 6.3 フィールド単位のAuthority Map

`authority_map.py` はfieldごとのclassification、store、writer、binding、read source、cache、fallback、migration stateを検証する。authoritative classificationでは、非権威storeへの昇格を拒否し、各fieldにexactly one authoritative writerを要求する。[内7]

この設計は「Google Driveにあるから正本」「DBの値だから正本」といった物理場所依存の権威付けを避ける。将来複数Subjectが接続する場合も、共有されたRelationが相手の内部Context全体のwriter権限を得ないための基礎になる。

## 6.4 Source-gated共有状態

`shared_state.py` はContext Selection、Context Application、Delivery、Owner Outcome、Growth Correctionを別のstateとして扱い、書込み前にAuthority MapとSource staged commitの一致を確認する。[内11]

共有DBへはopaque ID、revision、closed code、hash、time、reference等を入れ、raw会話、人物名、秘密値等を禁止する。この構造は、共有状態を巨大な個人情報DBにしないための実装上の防波堤である。

## 6.5 文脈推論とRelationの分離

`context_reasoning.py` はProvider-neutralかつgraph-neutralな境界を持つ。Relation Graphは一つの内部Strategyであり、外部consumerはcanonical proposal setを受け取る。`ZERO_DERIVED_NORMAL`、`INSUFFICIENT_EVIDENCE`、`FAILED_SAFE`等を正常に区別し、Contextを無理に生成しない。[内8]

`relation_operational.py` はさらに、RelationをそのままContextへ変換しないことを明示する。受理済みEvidenceだけを探索し、Relation経由で見つけたContextも、元Source、lifecycle、time、privacy、Authority等のGateを通る。[内12]

これは「Relationがあるから情報を使ってよい」という誤りを防ぐ。Relationは関連性・経路のEvidenceであり、利用許可ではない。

## 6.6 Relation受理の独立ライフサイクル

PostgreSQLの `020_relation_admission.sql` では、Relation候補について、Validation Event、Review Event、Admission Event、Admitted Relation Evidenceが分離され、payload hash、Source snapshot、Authority、generation、writer、sink、fencing tokenで拘束される。[内13]

受理されたRelation Evidenceはupdate/deleteを拒否するtriggerでappend-only化される。さらに `NO_RELATION` と `INSUFFICIENT_EVIDENCE` が正常なterminal resultとして保存される。

この実装は、LLMが関係らしい文章を生成したことと、システムが利用可能なRelationとして受理したことを分ける。

## 6.7 実作業Growth Loop

`live_ordinary_growth_loop.py` は、可視Task identity、Context arm、実作業開始、Delivery、Owner Outcome、Utilization、Growthを分ける。[内14]

`outcome_growth_correction.py` は、採用、部分採用、修正、却下と、`USED_AS_IS`、`USED_WITH_REVISION`、`NOT_USED`等の実利用状態を別に扱い、Context選択や実行方法へのCorrectionをappend-onlyで記録する。[内15]

現行Personal Tora Profileが定義する最初の完成線は、

```text
Source
→ Context Application
→ 因果近似
→ Action / Delivery
→ Outcome
→ Correction
→ 後続類似task
→ 予防可能な修正の減少、または条件差に応じた適切な差別化
```

である。[内6] テスト件数や保存量ではなく、後続作業で実際に差が出ることを要求している点が特徴である。

## 6.8 自然言語Owner ingress

`ordinary_owner_ingress.py` はOwnerの自然言語を既存のDispatch、Context、Outcome、Relation経路へ投影する薄い境界であり、raw Owner本文を永続化せずhashと限定された派生fieldだけを保持する。[内16]

この実装は、自然言語AIを「すべてを所有する万能Planner」にせず、既存state ownerへ意味を渡すadapterとして扱う。

## 6.9 Source intake

`live_source_semantic_intake.py` はCodex rolloutをread-only Providerから増分取得し、screened raw Sourceをlocal runtimeへ保持し、高信号区間を交換可能なsemantic workerへ渡す。[内17] Source captureだけではSemantic completionやOutcome completionを主張しない。

この「Source取得 ≠ 意味理解 ≠ Relation成立 ≠ Context利用 ≠ Outcome」という分離は、本稿の主体間連合へ拡張する際にもそのまま必要になる。

## 6.10 実行Providerの交換境界

`codex_sdk_controller.py` はCodexを現在のOwner-facing transportとして使用するが、Planning、Scheduling、Context、Relation、Admission、Healthを所有しない。Provider-neutralな `OwnerTaskTransport` を定義し、Codexは一つのadapterとする。[内18]

この設計は、ToraOSを特定AI企業のアプリケーションへ固定しないために重要である。

## 6.11 現在の未完成境界

最新PR #36はCodex Hook payload bridgeを追加したが、Hook、Scheduled Task、productionを有効化していない。projection directory replacementのTOCTOU問題をP2として残し、unattended execution、production、Hook activationをSTOPとしている。[内19]

この状態は論文上重要である。ToraOSは多くの機構を実装しているが、**自動化の全経路がproduction運用済みではない**。

## 6.12 実装済みと未実装の整理

| 領域 | 2026-08-29時点 |
|---|---|
| Source / Derived分離 | 実装あり |
| field-level Authority | 実装あり |
| Context Selection / Application | 実装あり |
| Relation derivation / validation / review / admission | 実装あり |
| Relation-assisted Context | 実装あり |
| Delivery / Owner Decision / Utilization / Outcome分離 | 実装あり |
| Outcome → Correction | 実装あり |
| 後続類似taskへのfeedback経路 | 実装・受入段階、自然再発Evidenceは別管理 |
| 自然言語Owner ingress | 実装あり |
| Codex SDK transport | 実装あり |
| Hook完全自動化 | 非activated、STOP条件あり |
| Person/Company/Communityの独立ToraOS複数instance | 未実装 |
| Subject間Relation federation | 未実装 |
| 相互Relationのcross-instance handshake | 未実装 |
| DID/VC等とのpublic interoperability | 未実装 |
| 公開conformance suite | 未実装 |
| OSS license / public repository | 未決定・未公開 |
| Relationを使った社会的与信 | 研究仮説 |

# 7. 本稿が新たに統合するSubject-Centricモデル

## 7.1 過去のOPEN案との関係

ToraOS OPENの設計Trajectoryでは、2026年8月10日の一部資料に「Personal Node Only」という仮説が存在した。[内20] これは組織を巨大な人格へ擬人化しないための安全側仮説だった。

その後のv0.3では、Company、Community、Concept等をTora Subjectとして許しつつ、全SubjectへConstitution、Goal、Action、Growthを強制しないOptional Capabilityへ改訂された。[内5]

さらに現行普遍意味憲法は、Companyや組織化CommunityがSubjectになり得ることをCurrent Semantic Grammarとして認めている。[内1]

本稿はこのTrajectoryを踏まえ、最新の著者方向を次のように整理する。

> Personal、Company、Communityは異なる製品ではない。  
> **同一のToraOS Kernelが、それぞれ別Subjectについて独立して成立する。**

これは旧Personal Node Only仮説を歴史から消すのではなく、反証と改訂のTrajectoryとして保存した上での新しい上位仮説である。

## 7.2 第二インスタンスとしてのCompany Tora

Company Toraの意義は「Personal Toraの会社モード」を作ることではない。

Personal Toraで成立していた暗黙の前提、すなわちOwnerが一人、Goalの決定者が一人、Contextの境界が一つ、を別主体でも同じKernelが扱えるかを検証する**第二インスタンス試験**である。

Company Subjectでは、

- 代表者とSubjectを分ける
- RoleとActorを分ける
- 会社のDecisionと個人の意見を分ける
- 会社のOutcomeと個人のOutcomeを分ける
- Personal Contextを会社へ自動流入させない
- 会社のAuthorityをPersonal Toraが代行しない

ことが必要になる。

この試験に成功すれば、ToraOSが「一人の利用者専用AI」から「Subject-neutralなOS」へ抽象化できる最初のEvidenceになる。

## 7.3 第三インスタンスとしてのCommunity

Communityでは、さらに単一代表者、雇用契約、法的人格が存在しない場合がある。複数Goal、Dissent、暫定合意、脱退、再加入、未決状態が普通になる。

ここで同じKernelが成立すれば、SubjectはPersonやCompanyに限定されず、成立手続とCapabilityの組合せで多様な共同体を表せる可能性が高まる。

# 8. 相互Relationから生まれる関係価値

## 8.1 自己申告と他者から返されるRelation

主体が自分について保持するプロフィールは情報である。一方、他主体が自分について発行し、AuthorityとEvidenceを伴って返すRelationは、場合によって信用、資格、保証、権威、所属、委任を表す。

```text
Aが自分で書く：
A → MEMBER_OF → B

Bが返す：
B → HAS_MEMBER → A
```

後者があることで、Aの自己申告だけではない独立Evidenceが加わる。

さらに第三者Cが、Bの組織としての公式性やA-B関係を保証する場合、信用は一つの点数ではなくEvidence Pathとして説明できる。

```text
C → RECOGNIZES → B
B → APPOINTED → A
A → ACCEPTS_ROLE → B
```

## 8.2 与信・保証・権威への応用仮説

将来、金融機関、行政、資格機関、会社、地域団体等がToraOSまたは互換実装を持つ場合、Relationは以下を表し得る。

- 所属・役職
- 資格・認定
- 代表権・委任
- 契約関係
- 保証
- 支払・履行実績
- 推薦
- 継続的な取引関係
- 行政上の居住・登録関係

ただし、これを自動的に「信用点80」のような値へ変換してはならない。住宅契約に必要なRelationと医療アクセスに必要なRelationは異なる。

ToraOSの普遍意味憲法も、報酬、人事、補償、商業利用、権利制限等を、該当Subjectが目的、Scope、Authority、説明・訂正手続を採用した場合だけ接続する任意Decision layerとしている。[内1]

## 8.3 関係資本は譲渡不能とは限らないが、推移可能でもない

価値あるSubjectと双方向に接続されることは、当該主体の社会的位置を説明するEvidenceになり得る。しかし「信用ある会社に所属しているから、その人の全行動を信用できる」とはならない。

関係価値は、関係種別・Scope・時点・Authority・Outcomeに限定される必要がある。これを無視すると、権威の借用、関係洗浄、評判ロンダリングが起きる。

# 9. 実結果駆動の「成長」

## 9.1 記憶量を成長としない

ToraOSの現行要件は、保存量、ファイル数、Relation数、Graph密度、テスト件数を成長指標にしない。[内4][内6]

本稿ではAI OSの成長を次のように定義する。

> **過去のSource、判断、違和感、失敗、Outcomeが、関連する後続場面でより良い初回行動または適切な差別化を生み、その結果を再び検証できること。**

同じ修正が減ることは一つのEvidenceだが、過去に固定されて柔軟性を失うことは成長ではない。

## 9.2 Outcomeは主体ごとに異なる

同じActionでも、Person、Company、Communityから見たOutcomeは異なり得る。

例えば会社にとって業務効率が上がっても、個人に過度な負担が生じる場合、二つを一つの総合点へ相殺しない。現行Personal Profileも各SubjectのOutcome Viewを別に保持すると定めている。[内6]

これはSubject federationで重要になる。複数主体が同一現実Actionに関係した時、Outcomeを一つの「世界の正解」にしない。

# 10. 「擬似ワールド」としての分散Subject連合

## 10.1 巨大な一個のToraOSではない

本稿の長期仮説は、全世界を一つの中央ToraOSへ収容することではない。

```text
ToraOS Subject A  ←→  ToraOS Subject B
       ↑                    ↓
       └────→  OtherOS C  ←─┘
```

異なる主体、異なる実装、異なる運営者が、それぞれ独立状態を持ったまま、許可されたRelation、Claim、Credential、Artifactを交換する。

したがって最終的な成功は「全員がToraOSを使うこと」ではない。ToraOSが消え、より良いforkや全く別の実装が広がっても、互換可能なSubject-centric grammarが残れば構想上は成功である。

## 10.2 SaaS/SNSの役割変化仮説

現在は、

```text
SNSの中に人がいる
SaaSの中に会社がいる
```

という設計が一般的である。

主体中心の世界では、

```text
人・会社というSubjectの周囲に
SNS、SaaS、AI、決済、保存、行政サービスが接続する
```

という逆転が起こり得る。

これはSaaS/SNSが消えるという予言ではない。むしろ、**主体Identityと長期Contextを所有する場所から、能力を提供するAdapterへ相対化される**可能性を示す。この方向はSolidが既に提示しているアプリとデータの分離を、AIによる判断・Outcome層まで拡張する仮説と見ることもできる。

## 10.3 世界は一枚の真実Graphではない

この「擬似ワールド」は、一枚の世界知識グラフではない。

各Subjectが独立したTruth ViewとAuthorityを持ち、Relationによって重なり合うRelational Fieldである。相互に矛盾するRelationも、争いが現実に存在するなら両方保持する。

この設計は、一つの中央AIが「世界はこうである」と決める構造より、現実社会の複数主体性に近い。

# 11. 参加しない自由と社会的摩擦

## 11.1 非参加は「同じ便利さ」の保証ではない

Subject-centricな社会基盤が普及した場合、それを利用しない人が存在してもよい。しかし、利用しない選択に一切の摩擦や追加費用が生じないことまで保証する必要はない。

現在も、オンライン手続を使わず窓口へ行く、キャッシュレスを使わない、電子契約を使わない等の自由はあるが、時間、費用、利用可能サービスに差が生じることがある。

将来、行政手続、保険、雇用等で機械検証可能なRelationが一般化すれば、非参加者は紙証明、対面確認、追加審査等を必要とする可能性がある。

## 11.2 ただし非参加と排除を同一視しない

一方で、社会的に不可欠な公共サービスまで実質的に利用不能になる場合は、単なる技術選択ではなく法・政策・権利の問題になる。

ToraOS Coreが「どの代替経路を何円で保証するか」を世界共通に決めるべきではない。Coreが守るべきなのは、

- 接続・非接続をRelationとして明示できる
- 強制Relationを任意同意として偽らない
- AuthorityとEffectを辿れる
- 非参加者についてRelation欠如を自動的に低信用と解釈しない

といった意味上の境界である。

# 12. リスクと反証条件

## 12.1 監視基盤化

主体のSource、Relation、Outcomeが大量に結ばれるほど、利便性と同時に監視能力も高まる。特に「readの許可」と「inferの許可」を分けなければ、明示開示していない属性がRelation経路から推測される。

現行普遍意味憲法が `ingest / retain / read / use / infer / relate / disclose / prove` を別行為として扱うのは、この問題への重要な基礎である。[内1]

## 12.2 相互Relationの強制

雇用者や行政等、力の強いSubjectが「相互Relationを返さなければサービスしない」と迫ることはあり得る。形式上双方向でも、自発的同意とは限らない。

したがってRelationには、成立Procedure、Authority、強制性、異議・撤回経路等を表せる必要がある。

## 12.3 Sybilと偽公式Subject

permissionlessにSubjectを作れる場合、偽会社、偽資格機関、偽本人Subjectを大量生成できる。名前やSubject作成だけでOfficialityを与えてはならない。

DID/VC等の既存標準、現実Registry、第三者Recognition、Authority Pathの組合せが必要である。

## 12.4 Relation laundering

価値あるSubjectと形式的に接続することで、関係価値を不当に借用する攻撃が考えられる。Relation数・人気・短い経路だけで信用を計算すると、この攻撃に弱い。

## 12.5 単一Social Scoreへの退化

実装者が便利さのためにRelationを一つの点数へ集約すると、本稿のPluralityは簡単に失われる。これはToraOS思想に対する主要な反証・逸脱条件である。

## 12.6 AI推論の権威化

AIがRelation候補を生成できることと、そのRelationがCanonicalに採用されることを分けなければ、幻覚が社会関係へ昇格する。現行Relation admissionがValidation、Review、Admissionを分ける理由はここにある。[内13]

## 12.7 OSSのCaptureと分裂

公開後、特定企業による商標・ホスティング集中、互換性を壊すfork、Maintainer burnout、脆弱性管理等が起こり得る。OSS化は分散性を自動保証しない。

# 13. 評価計画

本稿の構想は、次の段階で反証可能にする。

## 13.1 E1：Personal Toraの再発Evidence

現行Personal Toraで、過去Correctionが自然に発生した後続類似Taskの初回Actionを変え、実Outcomeで改善が確認されること。

**失敗条件**：Contextが増えるだけで修正が減らない、または過去Contextの過剰適用が増える。

## 13.2 E2：第二Subjectインスタンス

Company等をSubjectとする第二ToraOSを、同じKernelで成立させる。

**成功条件**：Personal用の特別分岐をKernelへ大量追加せず、独立Source、Authority、Decision、Outcomeを保持できる。

**失敗条件**：Company化のために別OSを作る必要が生じる、またはPersonal Contextが暗黙流入する。

## 13.3 E3：相互Relation

Personal SubjectとCompany Subject間で、片方向Relationを独立作成し、双方のRelationが対応した時だけ相互Projectionを作る。

**成功条件**：片側取消、時点差、Role変更、第三者保証、矛盾を保持できる。

**失敗条件**：相互化のために一つの共有Truth Recordへ統合しなければならない。

## 13.4 E4：第三Subjectと複数主体Outcome

Community等の第三Subjectを追加し、同一Actionに対する異なるOutcome Viewを保持する。

## 13.5 E5：別実装との互換

ToraOSをforkした実装または独立実装が、Subject identity、Relation statement、provenance、revocation、disclosure等の最小grammarで相互運用する。

**このE5が成立して初めて、ToraOSが「製品」ではなく公開アーキテクチャへ進んだと言える。**

# 14. OSS公開の意味

## 14.1 完成してから公開する必要はない

ToraOSをOSS化する目的が完成製品の販売ではなく、Subject-centric AI OSという思想と実装可能性を世界へ置くことであれば、v1.0完成は公開の必須条件ではない。

むしろ公開時に、

- 実装済み
- 実験中
- 設計済み未実装
- 研究仮説
- 社会的未来予想

を明示すれば、未完成であること自体が研究状態になる。

## 14.2 Reference ImplementationとしてのToraOS

ToraOS OPENの成功条件を「ToraOSの利用者数」に置かない。

> ToraOSは、Subject-centric architectureの最初のReference Implementationであり得る。

forkされてもよい。別言語で書き直されてもよい。より使いやすい実装に置き換わってもよい。ToraOSという名称が消えても、主体が独立ContextとAuthorityを持ち、Relationで接続され、Outcomeから成長するという文法が残れば、著者の目的には合う。

## 14.3 公開前に最低限必要なもの

本稿の立場では、公開前に少なくとも次が必要である。

1. 公開対象コードからPersonal/Raw/Secretを除外する。
2. LICENSEを決定する。
3. READMEでCurrent実装とFuture Visionを分離する。
4. ManifestoまたはSemantic Constitutionの公開版を置く。
5. Subject、Relation、Authority、Outcomeの最小用語を定義する。
6. 既知の重大未実装・STOPを明示する。
7. 外部が反証・fork・比較できるIssue/Discussion経路を作る。

現在のprivate READMEはlicense未承認を明示しているため、このGateを越えるまではOSSと呼ばない。[内3]

# 15. 本研究の限界

第一に、ToraOSは現時点で一人の著者を中心に形成されたPersonal Toraが主要な実利用対象であり、複数独立Subjectの実連合は未実証である。

第二に、コードの多くはAI支援で開発されており、テストとFresh Reviewは存在するが、独立した学術研究チームによるコード監査や形式検証は未実施である。

第三に、CurrentコードのAuthority Mapはfield writerの技術的Authorityを扱う一方、本稿の社会的Authorityはより広い。両者の共通語彙と境界は今後さらに形式化が必要である。

第四に、Relationから信用、保証、権威が生じることは既存研究にも広く存在する。本稿が示す相互Relationモデルが既存のSSI、Web of Trust、VC、評判モデルより実際に優れるかは比較実験が必要である。

第五に、SaaS/SNSが主体中心へ再編されるという議論は未来予想であり、本稿の実装証拠から導ける結論ではない。

第六に、行政・医療・雇用等への適用は技術だけで決まらない。法、倫理、差別、行政負担、権利保障、制度設計を別分野の専門家と共同で検討する必要がある。

# 16. 考察

ToraOSの開発は、AIに「もっと覚えさせたい」という単純な要求から始まった。しかし、長期利用で本当に必要になったのは保存容量ではなかった。

誰が言ったのか。何が原情報なのか。AIが解釈しただけなのか。誰が決定する権限を持つのか。その判断はいつ有効だったのか。実際に使ったのか。結果はどうだったのか。次回は何を変えるべきか。

この問いを一つずつ分けると、AIは「巨大な記憶付きチャット」ではなく、Subjectの継続状態を扱うOSに近づく。

さらにSubjectをPersonからCompany、Communityへ一般化すると、Personal AIの問題だったものが社会構造の問題へ変わる。主体ごとのContextを中央へ統合しないまま、Relationを通じて社会的に接続する必要が生まれるからである。

ここでRelationは単なるKnowledge Graph edgeではなくなる。自己申告、相手からの確認、第三者保証、権限、時点、Outcomeを持つ関係の束が、現実の信用や権威を説明する経路になる可能性がある。

一方、この構造は監視、排除、Social Score、権威の集中にも転用できる。したがってToraOSの価値は「何でもつながる」ことではなく、**つながる意味、根拠、権限、開示、撤回、反証を失わないこと**にある。

# 17. 結論

本稿は、ToraOSを単なるPersonal AI OSではなく、**主体中心型・進化型AI OS**として再定義した。

中心原則は次の通りである。

1. **一つのOS、任意の主体**：Person、Company、Community等はOSの別製品ではなくSubjectの種類である。
2. **主体ごとに独立したContextとAuthority**：同じEntityを知っていても、各Subjectの知識、正本、判断、秘密は別である。
3. **Relationは方向付き主張**：A→BとB→Aを別に保持し、相互性は推定せずEvidenceからProjectionする。
4. **相互Relationは関係価値を生み得る**：信用、保証、権威、資格、所属等を中央Scoreではなく検証可能なRelation Pathとして扱う。
5. **成長はOutcomeで判定する**：記憶量やGraph量ではなく、過去のEvidenceが次のActionを改善し、その結果が再びCorrectionへ戻ることを成長とする。
6. **世界は単一OSに所有されない**：独立Subjectと異なる実装がRelationで接続される分散Relational Fieldを目指す。
7. **ToraOSそのものの普及を最終目的にしない**：公開仕様、Reference Implementation、fork、独立実装を通じて思想が残ればよい。

現行コードには、この構想を支えるSource分離、field Authority、Context、Relation admission、Outcome、Correction等の実装が既に存在する。一方で、multi-subject federationと相互Relationの社会的利用は未実装である。

したがって本稿の結論は「ToraOSが未来の世界OSである」ではない。

> **主体自身がAIの文脈と権限を持ち、独立した主体同士が検証可能な関係によって接続され、実結果から継続的に更新されるアーキテクチャは、現在のプラットフォーム中心型AIとは異なる有力な研究方向である。ToraOSは、その仮説を実コードと実利用から検証する一つのReference Implementationである。**

この仮説が誤っていれば、公開されたコードと設計から反証されればよい。より良い実装が生まれれば置き換わればよい。ToraOS OPENの目的は、完成品を囲い込むことではなく、この問いを検証可能な形で世界に置くことにある。

---

# 内部一次資料

**[内1]** ToraOS, 「Universal Semantic Constitution / 寅Core憲法」, revision `TOROS-UNIVERSAL-SEMANTIC-CONSTITUTION-20260812-006`, Current Authority Layer 1, 2026.

**[内2]** ToraOS, 「寅OS構想・実装準備チャット」過去チャット分析ログ, source date 2026-05-27.

**[内3]** ToraOS private repository, `imprint283-boop/toraos-shadow-harness`, main commit `3c4ccac069034b75f776b0b0109b9964f5003a5a`, README and repository tree, accessed 2026-08-29.

**[内4]** ToraOS, 「ToraOS 要求・要件定義書 v1.2」, document `TOROS-RD-20260719-001`, adopted 2026-07-19.

**[内5]** ToraOS, 「寅OS OPEN 要求・意味定義書 v0.3 統合版」, revision `TOROS-OPEN-V03-20260810-001`, noncanonical future candidate, 2026-08-10.

**[内6]** ToraOS, 「Personal Tora Constitution / Profile」, revision `TOROS-PERSONAL-TORA-CONSTITUTION-PROFILE-20260825-008`, Current Authority Layer 2, 2026.

**[内7]** ToraOS source code, `toraos_shadow/authority_map.py`, commit `3c4ccac...`, 2026-08-29.

**[内8]** ToraOS source code, `toraos_shadow/context_reasoning.py`, commit `3c4ccac...`, 2026-08-29.

**[内9]** ToraOS, `AUTONOMOUS_CONTEXT_TRAJECTORY_GROWTH_LOOP_CONTRACT.md`, revision `TOROS-AUTONOMOUS-CONTEXT-GROWTH-LOOP-20260826-001`, 2026.

**[内10]** ToraOS, 「CURRENT_AUTHORITY_REGISTRY.md」, revision `TOROS-CURRENT-AUTHORITY-REGISTRY-20260828-038`, 2026-08-28.

**[内11]** ToraOS source code, `toraos_shadow/shared_state.py`, commit `3c4ccac...`, 2026-08-29.

**[内12]** ToraOS source code, `toraos_shadow/relation_operational.py`, commit `3c4ccac...`, 2026-08-29.

**[内13]** ToraOS source code, `sql/postgresql/020_relation_admission.sql`, commit `3c4ccac...`, 2026-08-29.

**[内14]** ToraOS source code, `toraos_shadow/live_ordinary_growth_loop.py`, commit `3c4ccac...`, 2026-08-29.

**[内15]** ToraOS source code, `toraos_shadow/outcome_growth_correction.py`, commit `3c4ccac...`, 2026-08-29.

**[内16]** ToraOS source code, `toraos_shadow/ordinary_owner_ingress.py`, commit `3c4ccac...`, 2026-08-29.

**[内17]** ToraOS source code, `toraos_shadow/live_source_semantic_intake.py`, commit `3c4ccac...`, 2026-08-29.

**[内18]** ToraOS source code, `toraos_shadow/codex_sdk_controller.py`, commit `3c4ccac...`, 2026-08-29.

**[内19]** ToraOS GitHub Pull Request #36, “Add nonactivated Codex Hook payload bridge”, merged into commit `3c4ccac...`, 2026-08-29 JST.

**[内20]** ToraOS, 「寅OS OPEN 実証・反証・公開Gate v0.1」, revision `TOROS-OPEN-GATE-20260810-001`, future research plan, 2026-08-10.

# 外部参考文献

**[1]** E. Mansour, A. V. Sambra, S. Hawke, M. Zereba, S. Capadisli, A. Ghanem, A. Aboulnaga, T. Berners-Lee, “A Demonstration of the Solid Platform for Social Web Applications,” *Proceedings of the 25th International Conference Companion on World Wide Web*, pp. 223-226, 2016. DOI: 10.1145/2872518.2890529.

**[2]** Solid Community Group, “Solid Protocol,” Version 0.11.0, Solid Project, accessed 2026-08-29.

**[3]** W3C, “ActivityPub,” W3C Recommendation, 23 January 2018.

**[4]** W3C, “Decentralized Identifiers (DIDs) v1.1: Core architecture, data model, and representations,” Candidate Recommendation Snapshot, 5 March 2026.

**[5]** W3C, “Verifiable Credentials Data Model v2.0,” W3C Recommendation, 15 May 2025.

**[6]** W3C, “Bitstring Status List v1.0,” W3C Recommendation, 15 May 2025.

**[7]** W3C, “PROV-O: The PROV Ontology,” W3C Recommendation, 30 April 2013.

**[8]** Z. Zhang, X. Bo, C. Ma, R. Li, X. Chen, Q. Dai, J. Zhu, Z. Dong, J.-R. Wen, “A Survey on the Memory Mechanism of Large Language Model based Agents,” arXiv:2404.13501, 2024.

**[9]** J. Zheng, C. Shi, X. Cai, Q. Li, D. Zhang, C. Li, D. Yu, Q. Ma, “Lifelong Learning of Large Language Model based Agents: A Roadmap,” arXiv:2501.07278, 2025.

**[10]** V. Vizgirda, R. Zhao, N. Goel, “SocialGenPod: Privacy-Friendly Generative AI Social Web Applications with Decentralised Personal Data Stores,” arXiv:2403.10408, 2024.

**[11]** A. Jøsang, R. Ismail, C. Boyd, “A survey of trust and reputation systems for online service provision,” *Decision Support Systems*, Vol. 43, No. 2, pp. 618-644, 2007. DOI: 10.1016/j.dss.2005.05.019.

**[12]** K. Avrachenkov, D. Nemirovsky, K. S. Pham, “A survey on distributed approaches to graph based reputation measures,” *SMCTOOLS*, 2010. DOI: 10.4108/smctools.2007.2027.

**[13]** A. Narayanan, V. Toubiana, S. Barocas, H. Nissenbaum, D. Boneh, “A Critical Look at Decentralized Personal Data Architectures,” arXiv:1202.4503, 2012.

**[14]** Z. Lin, X. Hao, R. Fu, S. Cui, K. Chen, C. Li, Z. Li, F. Xiong, “A Survey on Long-Term Memory Security in LLM Agents: Attacks, Defenses, and Governance Across the Memory Lifecycle,” arXiv:2604.16548, 2026.

---

## 著者注記

本稿は著者個人の研究・開発活動を記述するものであり、著者が関係する企業、法人、団体、行政機関等の公式見解を示すものではない。実在組織名を例示する場合も、当該組織がToraOSを採用・承認・運用していることを意味しない。
