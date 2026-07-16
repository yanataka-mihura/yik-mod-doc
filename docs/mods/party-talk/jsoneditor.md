# JsonEditorについて

!!! warning "自分用なので動作保証はありません。大枠づくり程度に考えてください。"
    ウイルスチェック等はしっかり行い、動かない場合はあきらめてください。

作者はJsonを作るエディターをcodexに作ってもらって作業をしています。  
メンテナンス予定はほぼありませんが、以下のボタンからZipダウンロードして利用可能です。


[DL PartyTalk.JsonEditor](download/PartyTalk.JsonEditor.zip){ .md-button .md-button--primary }

---

## PartyTalk.JsonEditor 簡易使い方

PartyTalk 用の `Data.json` を編集するための補助ツールです。
左のツリーで編集したい Target / Topic / Line / Sequence を選び、右の JSON エリアで内容を編集します。

## 起動後にできること

- `Open`
  - 既存の `.json` ファイルを開きます。
- `Import Excel`
  - 旧 Excel 形式の `.xlsx` を読み込み、JSON 構造に変換して現在のドキュメントとして開きます。
  - 既存 JSON へのマージはしません。
- `Save`
  - 現在の JSON 全体を保存します。
- `Apply`
  - 右側の JSON エリアで編集した内容を、選択中のノードへ反映します。
- `Check Schema`
  - `talk.editor.schema.json` で緩く検証します。
  - schemaにないプロパティは警告として表示します。

## 基本編集

1. `Open` で `Data.json` を開きます。
2. 左のツリーから編集したい項目を選びます。
3. 右側に選択中の JSON 断片が表示されます。
4. 右側の JSON を編集します。
5. `Apply` を押して反映します。
6. `Save` でファイルへ保存します。

`Apply` せずに別項目へ移動しようとすると、反映するか確認されます。

## ツリー表示

左ツリーは以下の形で表示されます。

```text
TargetId / TargetType
  TopicId - Topic説明
    Lines
      Textの先頭30文字
    TalkSequences
      Sequence #1 (Weight: 1)
        AdditionalTargets
          TargetId / TargetType
        Lines
          SpeakerId: Textの先頭30文字
```

画面上部のパンくずには、現在選択中の `TargetId / TargetType` と `TopicId / 説明` が表示されます。

## 追加

左ツリー上部の `Add...` ボタン、またはツリーの右クリックメニューから追加できます。

- `Target`
  - 空の Target を追加します。
- `Topic`
  - 空の Topic を現在の Target に追加します。
- `Catalog Topic`
  - `TopicCatalog.csv` から Topic を選んで追加します。
  - 既に同じ `TopicId` がある場合は追加せず、その Topic を開きます。
- `Line`
  - 単独発言の Line を現在の Topic に追加します。
- `Sequence`
  - 連続発言の TalkSequence を現在の Topic に追加します。
  - 最低限成立する仮の SequenceLine も1つ作成します。
- `Sequence Line`
  - 現在の TalkSequence に SequenceLine を追加します。
- `Additional Target`
  - 現在の TalkSequence に AdditionalTargets の要素を追加します。

## 追加ショートカット

```text
Ctrl+1 Target
Ctrl+2 Topic
Ctrl+3 Catalog Topic
Ctrl+4 Line
Ctrl+5 Sequence
Ctrl+6 Sequence Line
Ctrl+7 Additional Target
```

利用できない状態でショートカットを押した場合は追加せず、音を鳴らして下部メッセージに追加できない旨を表示します。

## 削除

削除は以下から行えます。

- 上部の `Delete`
- ツリーの右クリックメニュー `Delete`
- ツリー項目選択中の `Delete` キー

右側 JSON エリアで編集中の `Delete` キーは、通常のテキスト削除として動きます。

`AdditionalTargets` の最後の要素を削除した場合、空の `[]` は残さず `AdditionalTargets` ごと削除します。

## Excel インポート

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

## 注意点

- 保存時、JSONコメントは保持されません。
- 未知プロパティは、編集対象の JSON 断片を丸ごと置き換えない限り保持されます。ただし未知プロパティはModで読み込むとErrorになります。
- このツールで作ったJSONがModで正しく動くことを保証しません。大枠作成ツールと思ってください。
- Excel へのエクスポートはありません。