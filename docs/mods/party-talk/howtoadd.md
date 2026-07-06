# うちのこキャラ追加方法

## 概要

自分のところの仲間や、プレイヤーについて会話定義を自分で起こしたい場合の説明になります。

Mod本体の会話定義に追記することもできますが、自作Modの入れ物を用意しておくと使い勝手がよくなります。


## PartyTalk用の自作Modを作る

まず、以下の通りにフォルダとXML、Jsonファイルを用意します。XMLとJsonはまだ中身は空でよいです。

ModRootフォルダ名はすきにつけてください。そのほかのフォルダ、ファイル名は固定です。

```md

- ModRoot/
  - PartyTalk/
    - PartyTalk.json
  - package.xml

```

### package.xmlを埋める

package.xmlの内容を埋めます。ElinでMod一覧を表示したときに出てくる名前などが設定されます。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Meta>
	<title>私用PartyTalkMod</title>
	<id>abcdefghijk</id>
	<author>私</author>
	<loadPriority>100</loadPriority>
	<description>
		aaa
	</description>
	<tags>General</tags><visibility>Private</visibility>
	<version>0.23.50</version>
</Meta>

```

- `title`: 任意のタイトルを入れます。ElinのMod一覧に表示される名前です。
- `id`: ユニークなIDを入れます。念のためユーザー名.partytalk.modなど、他と被らないものをつけてください。
- `author`: 適当
- `loadPriority`: ロード順らしい、そのまま
- `description`: 適当
- `tags`: そのまま
- `visibility`: 万が一Steamにアップロードしてしまった時の公開状態を表します。Privateにしておけば非公開なので安心。
- `version`: 対応するElinのバージョンを入れる。今のところ厳密に何かしているわけではないので現在のバージョンを入れてよい

### PartyTalk.json を埋める

ここが一番めんどくさいと思います。気合と根性で書いてください。

Mod本体のサンプルファイル、[おしゃべり会話定義の設定項目一覧](definition.md)等を参考にして書いていきます。

??? example "黒天使に適応されるサンプル"
    ```json
    {
    "Talks": [
        {
        "TargetId": "black_angel",
        "TargetType": "Id",
        "Topics": [
            {
            "TopicId": "LoadAfter",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ん、おかえり"
                },
                {
                "Weight": 1,
                "Text": "おそかったじゃない"
                }
            ]
            },
            {
            "TopicId": "ReturnHome",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ねぇ、羽を梳いてくれない？"
                },
                {
                "Weight": 1,
                "Text": "甘いもの食べたいな……"
                }
            ]
            },
            {
            "TopicId": "BossHere",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "へー、強そうじゃん"
                }
            ]
            },
            {
            "TopicId": "Festival",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "♪～（ご機嫌だ）"
                }
            ]
            },
            {
            "TopicId": "PlayerKilled",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "えっ……"
                },
                {
                "Weight": 1,
                "Text": "ちょっと、やだ…っ！"
                }
            ]
            },
            {
            "TopicId": "PlayerDeath",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "このおばか！！"
                }
            ]
            },
            {
            "TopicId": "KilledBoss",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "当然よ"
                },
                {
                "Weight": 1,
                "Text": "ま、こんなものね"
                }
            ]
            },
            {
            "TopicId": "PlayerPinch",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "下がってなさい！"
                },
                {
                "Weight": 1,
                "Text": "自分を大事にしなさいよ！"
                }
            ]
            },
            {
            "TopicId": "PlayerLvUp",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "おめでとう#pc"
                },
                {
                "Weight": 1,
                "Text": "まぁ、ほめてあげる"
                }
            ]
            },
            {
            "TopicId": "AtSleep",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "なに？ 子守歌でも必要なの？"
                },
                {
                "Weight": 1,
                "Text": "ん、おやすみ"
                }
            ]
            },
            {
            "TopicId": "AtSleep_Beside",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "いいから詰めなさいよ"
                },
                {
                "Weight": 1,
                "Text": "ん……（布団に潜り込んできた）"
                }
            ]
            },
            {
            "TopicId": "WakeUp",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "呆けてないで顔洗ってきなさい"
                },
                {
                "Weight": 1,
                "Text": "ふふ、寝ぐせ……"
                }
            ]
            },
            {
            "TopicId": "WakeUp_Beside",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ねぇ、もうちょっと……"
                },
                {
                "Weight": 1,
                "Text": "……あんまり見ないで"
                }
            ]
            },
            {
            "TopicId": "EnterNefia",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "私の出番よ！"
                },
                {
                "Weight": 1,
                "Text": "まっかせなさい！"
                }
            ]
            },
            {
            "TopicId": "Cuddled",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ちょ、なによ……もう"
                },
                {
                "Weight": 1,
                "Text": "んー？　へへ……"
                }
            ]
            },
            {
            "TopicId": "TARU",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "たるっ"
                },
                {
                "Weight": 1,
                "Text": "たーるっ"
                },
                {
                "Weight": 1,
                "Text": "たるるー！"
                },
                {
                "Weight": 1,
                "Text": "たる！"
                }
            ]
            },
            {
            "TopicId": "PTPinch",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "いい加減に……！"
                },
                {
                "Weight": 1,
                "Text": "やってくれたわね！"
                }
            ]
            },
            {
            "TopicId": "PTKilled",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "そんな、やだ……"
                },
                {
                "Weight": 1,
                "Text": "……#pc"
                }
            ]
            },
            {
            "TopicId": "ntyris",
            "Chance": 3,
            "Lines": [
                {
                "Weight": 1,
                "Text": "♪～（ご機嫌で飛んでる）"
                },
                {
                "Weight": 1,
                "Text": "ね、どこいくのよ"
                }
            ]
            },
            {
            "TopicId": "kapul",
            "Chance": 3,
            "Lines": [
                {
                "Weight": 1,
                "Text": "潮風はあんまりすきじゃないわ"
                },
                {
                "Weight": 1,
                "Text": "羽がべたつく……"
                }
            ]
            },
            {
            "TopicId": "void",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ほんとにいくの？"
                },
                {
                "Weight": 1,
                "Text": "ぞくぞくしてきたわ……"
                }
            ]
            },
            {
            "TopicId": "derphy_whore",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ねぇ、出ましょうよ……"
                },
                {
                "Weight": 1,
                "Text": "いらないでしょ、あなたには……"
                }
            ]
            },
            {
            "TopicId": "instance_arena",
            "Chance": 7,
            "Lines": [
                {
                "Weight": 1,
                "Text": "七面鳥撃ちよっ"
                },
                {
                "Weight": 1,
                "Text": "やってやろうじゃないの！"
                }
            ]
            },
            {
            "TopicId": "instance_arena2",
            "Chance": 7,
            "Lines": [
                {
                "Weight": 1,
                "Text": "七面鳥撃ちよっ"
                },
                {
                "Weight": 1,
                "Text": "やってやろうじゃないの！"
                }
            ]
            },
            {
            "TopicId": "instance_harvest",
            "Chance": 7,
            "Lines": [
                {
                "Weight": 1,
                "Text": "……私いやよ？"
                }
            ]
            },
            {
            "TopicId": "PlayerTired",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ほら、やすみましょ？"
                },
                {
                "Weight": 1,
                "Text": "お疲れみたいね"
                }
            ]
            },
            {
            "TopicId": "PlayerExhausted",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ちょっと！　無理しないの！"
                }
            ]
            },
            {
            "TopicId": "PlayerSleepy",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ん、眠いの？"
                }
            ]
            },
            {
            "TopicId": "PlayerVerySleepy",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ほら、もう寝なさいよ"
                }
            ]
            },
            {
            "TopicId": "PlayerHungry",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "小腹がすいてきたわ"
                },
                {
                "Weight": 1,
                "Text": "何か食べましょ"
                }
            ]
            },
            {
            "TopicId": "PlayerVeryHungry",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ご飯はちゃんとしなさいよ"
                }
            ]
            },
            {
            "TopicId": "PlayerBurden2",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "ほーら、がんばれ♡"
                }
            ]
            },
            {
            "TopicId": "PlayerOverweight",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "危ないわよ！"
                },
                {
                "Weight": 1,
                "Text": "ねぇ、大丈夫なの……？"
                }
            ]
            },
            {
            "TopicId": "FindDaddy",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "かもはっけーん！"
                },
                {
                "Weight": 1,
                "Text": "ふふ、やってやるわ"
                }
            ]
            },
            {
            "TopicId": "DrinkMilk",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "変態！"
                },
                {
                "Weight": 1,
                "Text": "……（赤面してぷるぷるしてる）"
                }
            ]
            },
            {
            "TopicId": "MyPanty",
            "Chance": 10,
            "Lines": [
                {
                "Weight": 1,
                "Text": "……み、みないで"
                },
                {
                "Weight": 1,
                "Text": "…？！#newlineこっちみんな！！"
                }
            ]
            }
        ]
        }
    ]
    }
    ```


過去にExcelで作っていたりする場合は[ExcelからJSONへのおしゃべり定義ファイルの移行案内](excel2json.md)ページも参照してください。

未保障ですが[ツール](jsoneditor.md)もあります。