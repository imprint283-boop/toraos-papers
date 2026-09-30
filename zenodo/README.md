# Zenodo情報の準備

[metadata.candidate.json](metadata.candidate.json) は人が確認するための情報案です。JSONとして読めることと、Zenodoへの登録に必要な情報が揃っていることは別です。ライセンス空欄は有効な設定ではありません。P1の著者・執筆日と公開範囲の本人判断も残っています。publication/otherは文書集の登録区分案です。

本ファイルはroot `.zenodo.json` ではないため、GitHub連携で自動取り込みされません。公開許可とライセンス等の確定後、AIが値を確定しroot `.zenodo.json`へ転記してからリリース工程へ進みます。CITATION.cffとroot `.zenodo.json`の両方がある場合、Zenodoは `.zenodo.json`だけを読み、CITATION.cffを無視します。[公式説明](https://help.zenodo.org/docs/github/describe-software/zenodo-json/)

ライセンスは必須で、Zenodoの既定値はCC BY 4.0です。未確定のまま既定値に任せて登録することはしません。[公式説明](https://help.zenodo.org/docs/deposit/describe-records/licenses/)

まだ公開日・公開版・DOIを設定していません。論文の執筆日を文書集の公開日へ転記しません。Zenodoへのログイン、連携設定、登録、DOI予約は行っていません。
