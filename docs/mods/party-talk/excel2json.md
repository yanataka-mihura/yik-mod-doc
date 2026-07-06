# ExcelからJSONへのおしゃべり定義ファイルの移行案内

## 移行は必要か？

excelは引き続き利用できます。

ただし、今後新しい機能はjsonのみの対応になることが多くなると思います。

## 特に自分で改修していない、PartyTalk本体のおしゃべり定義の移行方法は？

Mod本体フォルダに作成されている以下のファイルを削除すると次回起動時にSamplePartyTalk.jsonがリネームコピーされて読み込まれます。

配置場所: `～\Steam\steamapps\workshop\content\2135150\3384121582\PartyTalk.xlsx`

## Jsonでしかできないことは？

202607時点（json以降タイミング）では以下の通りです

- Chanceの個別適用: Excelではすべてのキャラが同一のChanceを使用します
- NoGakiConvertフラグ: Excelでは牙姫はザコ会話縛りを解除できません
- Sound再生: Jsonでのみ再生可能です（非保障機能）
- Textの重みづけ: Weight指定はExcel不可で、一律同じ確率でCell内のTextが抽選されます。
- Cooldown指定: Excelでは常に0（クールダウン指定なし）となります


## 自作・改修したExcelおしゃべり定義の移行方法は？

方法は3種類あります

- サンプルをもとに気合でJsonを書く
- 定義ファイルと一緒に元ExcelをChatGpt等に投げ依頼する
- 非保証のJsonエディタツールを試してみる

