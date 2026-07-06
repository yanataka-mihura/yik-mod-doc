# JsonEditorについて

!!! warning "自分用なので動作保証はありません。大枠づくり程度に考えてください。"
    ウイルスチェック等はしっかり行い、動かない場合はあきらめてください。

作者はJsonを作るエディターをcodexに作ってもらって作業をしています。  
メンテナンス予定はほぼありませんが、以下のボタンからZipダウンロードして利用可能です。


[DL PartyTalk.JsonEditor](download/PartyTalk.JsonEditor.zip){ .md-button .md-button--primary }

---

## PartyTalk.JsonEditor 簡易使い方

PartyTalk 用の `PartyTalk.json` を編集するための補助ツールです。
左のツリーで編集したい Target / Topic / Line を選び、右の JSON エリアで内容を編集します。

### 起動後にできること

- `Open`
  - 既存の `.json` ファイルを開きます。
- `Import Excel`
  - 旧 Excel 形式の `.xlsx` を読み込み、JSON 構造に変換して現在のドキュメントとして開きます。
  - 既存 JSON へのマージはしません。
- `Save`
  - 現在の JSON 全体を保存します。
- `Apply`
  - 右側の JSON エリアで編集した内容を、選択中のノードへ反映します。

### 基本編集

1. `Open` で `Data.json` を開きます。
2. 左のツリーから編集したい項目を選びます。
3. 右側に選択中の JSON 断片が表示されます。
4. 右側の JSON を編集します。
5. `Apply` を押して反映します。
6. `Save` でファイルへ保存します。

`Apply` せずに別項目へ移動しようとすると、反映するか確認されます。

### ツリー表示

左ツリーは以下の形で表示されます。

```text
TargetId / TargetType
  TopicId - Topic説明
    Textの先頭30文字
```

画面上部のパンくずには、現在選択中の `TargetId / TargetType` と `TopicId / 説明` が表示されます。

### 追加と削除

上部ボタン、またはツリーの右クリックメニューから操作できます。

- `Add Target`
  - 空の Target を追加します。
- `Add Topic`
  - 空の Topic を現在の Target に追加します。
- `Add Catalog Topic`
  - `TopicCatalog.csv` から Topic を選んで追加します。
  - 既に同じ `TopicId` がある場合は追加せず、その Topic を開きます。
- `Add Line`
  - 空の Line を現在の Topic に追加します。
- `Delete`
  - 選択中の Target / Topic / Line を削除します。

### Excel インポート

`Import Excel` で `.xlsx` を読み込めます。

対応形式:

- 1行目はヘッダー
- A列: `TopicId`
- B列: `Chance`
- C列以降の1行目: `TargetId`
- `TargetType` はすべて `SimpleName`
- 空セルは無視
- セル内の改行ごとに Line を作成
- `@{portraitId}` がある場合、最初のものを `Portrait` に使用
- `@{portraitId}` は Text からすべて除去

インポート後は、通常の `Save` で `.json` として保存します。

### 注意点

- 保存時、JSONコメントは保持されません。
- 未知プロパティは、編集対象の JSON 断片を丸ごと置き換えない限り保持されます。ただし未知プロパティはModで読み込むとErrorになります。
- このツールで作ったJSONがModで正しく動くことを保証しません。大枠作成ツールと思ってください。
- Excel へのエクスポートはありません。
