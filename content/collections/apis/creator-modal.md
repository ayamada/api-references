---
title: 作者情報を表示する
slug: creator-modal
description: RPGアツマールのゲームの作者情報が記載されたダイアログを表示することができます。
---

## 概要
アツマール上でゲームを投稿している作者の情報を表示する機能です。ゲームを作成しているご自身の情報または、IDで指定した任意の作者の情報を表示できます。
作者情報にはアツマール設定ページで設定できる、プロフィール、Twitter、サイトURLのほか、その作者の関連ゲームも含まれます。

### どんなことができるの？

![作者情報の表示](/images/creator_modal_sample1.png)

機能を実行した際に、スクリーンショットのようなウィンドウを開きます。以下のような利用を想定しています。

- ゲーム内作者情報ボタンからご自身の情報を表示する
- ゲーム作成に関わった他の作者の情報を表示する

### アツマール公式での利用例

アツマール公式では例えば次のゲームでこの機能を利用しています。

- [ガタガールsp. 阿比留中生物部活動レポート](https://game.nicovideo.jp/atsumaru/games/gm7318)
  - タイトル画面での「クレジット」内の「info」ボタン


## 設置方法

作者情報ダイアログを利用するには下記2つの方法が利用できます。

方法 | 場所
:---|:---
アツマール公式プラグイン | [Github](https://github.com/atsumaru/mv-plugins/blob/master/plugins/AtsumaruCreatorInformationModalExperimental.js)
アツマール API | -

## 公式プラグインの利用方法

公式プラグインで作者情報を表示するためには、以下のようにします。

1. プロジェクトのプラグインフォルダに [AtsumaruCreatorInformationModalExperimental.js](https://raw.githubusercontent.com/atsumaru/mv-plugins/master/plugins/AtsumaruCreatorInformationModalExperimental.js) を右クリックし「保存」して設置
1. イベントに `DisplayCreatorInformationModal` プラグインを設定
1. プラグインコマンドでモーダル表示コマンドの設定。および情報表示するユーザIDの指定(任意)

![作者情報表示プラグイン利用例](/images/creator-modal_plugin_sample.png)

<br>


プラグインコマンドは

```
DisplayCreatorInformationModal {niconicoUserId}
```

と記載してください。 `{niconicoUserId}` 部分は省略可能で、省略した場合はプラグインを設置しているゲームの作者自信の情報が表示されます。自分以外の作者情報を表示したい場合は、`{niconicoUserId}` にniconicoユーザIDを指定することも可能です。

### プラグインコマンド例

#### 現在のゲームの作者情報(=自分の作者情報)を表示する
```
DisplayCreatorInformationModal
```


#### ニコニコユーザーID 64341294 のユーザーの作者情報を表示する
```
DisplayCreatorInformationModal 64341294
```


## APIを利用した作者情報の設置方法

### 作者情報API
メソッド | window.RPGAtsumaru.experimental.popups.displayCreatorInformationModal(niconico_user_id)
:---|:---
説明 | 引数のniconico_user_idにniconicoユーザIDをint値で渡すことにより、作者情報ダイアログを表示するメソッド。<br>引数に渡す文字列の形式は整数で、省略(null)も可能。省略した場合は実行しているゲームの作者情報を表示。
引数 | niconicoユーザID(整数)。またはnull
戻り値 | 無し
リリース日 | 2018/07/02
更新日 | 2018/08/02
