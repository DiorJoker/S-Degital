# S-Degital

# _____________________________________________



# どんなオリアプを作る？

### 結論

`職場の課題を解決するもの`

### もう少し、補足すると

`仕事現場とそれ以外の時間の課題を解決するもの`

# 目標/ゴール

`WEBエンジニアとして就職すること`


# 背景

私は、`交通警備の会社`で働かせていただいております。

下記は、私の働いている会社の特徴です。

- 警備、管制、事務という３つの部署がある
- 警備の仕事は、建築工事や土木工事の現場に出向き、**現場**で警備業務
- 管制の仕事は、**警備員**の明日の現場を決める業務
- 事務の仕事は、何をやってるか私は知らない



# 超具体的に説明していく

重要になってくるのは、２つ

- 管制の仕事
- 各現場での警備員の隊長


です。

## 警備員

- 各現場では、必ず1名、隊長が必要
- 現場ごとに、必要な警備員の数は異なり、少ないところだと1名、多いところだと20名を超える現場もある
- 8名現場の場合、1名が隊長、7名が隊員
- 出勤時間、集合場所、勤務時間、業務内容、注意事項は、現場によって変わる（つまり、毎日違う）
- 同じ現場でも、毎日、隊員は入れ替わる（隊長は、同じ現場に継続して入ることが多い）



## 管制

- 6名ほど、在籍している
- 出勤時間は、9:00〜18:00




## その他

- この会社が保有している現場数は、260現場くらいある
- 事務員に関しては、今回触れない（唯一、勤怠管理、交通費管理、などは、今後、機能追加できそう）
- この会社の警備員の社員数（アルバイト含め）は、900名ほど



# では、何が問題で、どう解決したいのか

様々あります

### ①明日の現場の情報に誤りがあることがある



#### 主な原因

管制の人が、`送る度に、毎度、入力しないとならない`

#### 解決策

一度、現場を登録したら、DBに保存されるようにし、送信のたびに、入力しないようにする


### ②明日の指示が、てきとう/曖昧で、しっかりと把握できないことがしばしばある

管制6名は性格が違い、明日の現場の詳細の送り方（情報内容/フォーマット）が異なる


#### 具体例

##### ・明日の現場の基本的なフォーマット

```
案件名：
元請け会社：
出勤日：
集合場所：
集合場所住所：
集合時間：
開始時間：
勤務時間：
隊員数：
隊長氏名：
業務内容：
注意事項：
```

##### ・管制Aさんの送り方（真面目系人間）

```
お疲れ様です。
明日のスピーキングテストについての連絡です。

11/26（日）
①朝7時までに出発連絡を私（高橋）の携帯に下さい。通話でもLINEやショートメールのメッセージでも構いません。
高橋携帯　0?0-33?7-3?42

②8時30分に（可能なら8時20分までに）○田高校の正門前に集合。
三○高校　○区三○1-4-?6
最寄り駅は赤○橋駅です。

③2号制服の冬服上下、防寒着、キャップ、モール、警笛、白ベルト、白手袋（軍手不可）、黒革靴（指定の安全靴）、上履き（スリッパ等）、おにぎりやパンなどの昼食、飲み物

スニーカーは不可です。誘導灯、交通腕章、夜光チョッキは不要です。

試験のため、持ち物忘れ、遅刻は大問題に発展してしまうので、今日中に念入りに準備をお願いします。

不明点があれば、本日の19時までに連絡を下さい。よろしくお願いします。
```


##### ・管制Bさんの送り方（てきとう系人間）

```
2/1

8:30開始

ミルッ○ス
新菱○熱案件お願いします。


集合場所
東京テ○ポート駅を地上に出て

TOKYOのオ○ジェ前。
```

#### 解決策

①と同じだが、１度入力したら、もう一度その案件を送信するときは、使い回す


### ③集合場所と集合場所住所の照らし合わせがむずい/時間が勿体無い

どういうことかというと、

- 集合場所には、○○公園

と書いてあって、
- 集合場所住所には、○○区○○?-??-?

と書いてあるとして、

これを、Google検索すると、

**○○公園が出てこなくて、近くに似たような名前の公園が出てくることがある。**

・`そっちに行くと、集合場所が間違ってて、Yahooのマップで見ないと、出てこない公園があったり、`

それ以外にも、

・`集合範囲の指定が広くて、8名の隊員が、それぞれ別の場所で開始時刻まで待機している`

などの場合がある。




#### 解決策

DBに保存してある住所から、明日の現場情報として、マップ上にピンを立てる形で、視覚的にわかるようにし、全員が同じ場所で集合できるようにする


### ④毎度、現場が違うので、電車の経路を毎日確認しないといけない

#### 警備隊員の中で唯一私と話をしてくれる斉藤さんの証言

```
毎度、現場が変わるって、まじストレスじゃないですか？
```

#### これについて私の返答

```
いやぁ〜、ほんとそうっすよね...
でも、警備員の仕事だと、しょうがないっすもんね

...

あ！！！

でも、特定の部分をコンピュータにさせることで、少し、ストレス和らぐかもしんないっすよ！
```

#### となって、考えた機能が、

せめて、電車の経路だけは、毎度、自動で算出してくれて、

また、日時ごとに、交通経路を記録しておいてくれて、月末に提出するときのフォーマットで、出力/印刷できる機能



#### ポイント

ここで、明日の天気も取得できると良いと考えている


### ⑤警備隊員は意外と事務作業が多い

- 交通費の請求を交通費申請用紙で郵送（月末）
- シフトを紙で郵送（月末）
- 毎度、明日の現場を、Googleマップで確認
- 毎日、明日の移動経路を、NAVITIMEで確認
- 明日の天気を確認して、持ち物を入れ替える

これらを、自動で、システムがやってくれるとなれば、💖か・な・り💖助かる



### ⑥隊長の為の特別機能（もし、ここまでできると、尚良い。てか、１年かけてでも絶対にやる）


先ほど、**隊長が重要**と申しましたが、

それはなぜかと言うと、

隊長は、

・誰よりも早く来て、隊員が全員来るか、来なかったら管制に報告、また遅刻の管理/報告をしなくてはならない


また、もう一つ、**現場での課題の解決もできる**と書きました。

それは、

・隊員の勤務態度を見て、管制に報告
・必要な人員が揃っていない：管制に報告
（例えば、片側交互通行（通称、片交）の現場で、片交ができる人が1人も来ていない場合、追加の人材を要請しないといけない場合もある）
・その他、さまざまなことを、管制とコミュニケーションとらないとならない

#### これのシステムによる実現方法

1. 通話機能を付ける
1. 現場ごとに、掲示板機能
1. 管制の人しか見れない、隊員ごとの口コミページ
1. その現場に来る人に、事前に伝えたいことを隊長がメモとして書き込める



### ⑦交通費申請と勤怠申請の機能（これも、１年かけてでもやる）



### ⑧上番報告と下番報告の機能

色々、出てくるので、ここで一旦思考をストップ


# このアプリが与えられる付加価値

- 管制の方の残業時間と無駄な手間を少なくできる
- 私たち（警備員）は、仕事以外の時間に、業務のことから時間を奪われなくなる


# ここから、私の作成したいオリアプについてです。

## アプリ情報

サービス名：S-Degital
サービス：業務内外プロセス等効率化アプリケーション

まず、満たし方について

## 必須要件

### ①ユーザーと課題が定義されて、ユーザーの課題を解決するものになっている

####  まずユーザーは、と言うと

①管制の人ら
②警備の人ら

#### 課題は、と言うと

①管制の人らは、"仕事だから"とか"慣れ"とかで、やりきっているが、実はとてもめんどくさいことをしている
②そして、その被害が実は私たち（警備隊の人ら）に来ている
③仕事作業以外の、やることが意外と多い
④純粋に、このアプリを作るのが楽しみ

### ②プログラムが正しく動作する（エラー等で落ちない）

・`デバッガ`
・`静的解析ツール`
・`テストコード`

を使用して、エラー落ちを最大限なくす

### ③コードが読みやすい（静的解析ツールを通している）

・`リーブル`
・`達プロ`
・`プリプロ`

を参考にする

### ④見た目が一定整っている（デザイン崩れしていない）

デザインセンスは、ない

### ⑤独自ドメイン、HTTPS で Web 上に公開されている

できる、余裕

### ⑥GitHub 上にコードを公開し、プルリクを活用している

プルリクは、余裕でできる

### ⑦テストコードが少なくとも1つ以上書かれている

できる、やったこともある

## 加点要件

### ①SPA（Single Page Application） + API の構成である

多分、できる

### ②ユーザーが1人以上実際に使っている

多分、俺と斉藤さんは使う（斉藤さんと連絡先を交換しておく必要がある）

### ③運用（CICD,監視,セキュリティ,冗長性等）が考慮されている

・`GitHub Actions`
・`Railsガイドのセキュリティの箇所`
・`体系的に学ぶ安全なWebアプリケーションの作り方`


を参考にする

### ④パフォーマンスが悪くない

インフラ、セキュリティ、サーバー負荷、アクセス数考慮に挑戦したい

参考は、

・`Webエンジニアが知っておきたいインフラの基本`
・`体系的に学ぶ安全なWebアプリケーションの作り方`
・`マスタリングTCP/IP　入門編`
・`プロになるためのWeb技術入門`

**※推奨教材は、全部購入している**

### ⑤ストレスなく使え、UI/UXが良い

・`1冊ですべて身につくHTML ＆ CSSとWebデザイン入門講座`

を参考にする

### ⑥デザインが綺麗

・`1冊ですべて身につくHTML ＆ CSSとWebデザイン入門講座`

を参考にする

### ⑦モダンな技術（SPA,Docker,etc）を使っている

[これ](https://zenn.dev/riya_amemiya/articles/55d3918487e426)を参考に、

挑戦したい技術は、Next.js,Rails,Docker,TypeScript,TailwindCSS,GitHub Actions,Recoil,Jest,Notion

の技術を使用していく

### ⑧自分から作りたくて作っている

これは、当てはまる

業務改善をしたくて、作っている

### ⑨エンジニアになりたい理由とプロダクトのテーマにストーリー性がある

ストーリー性もあるし、
エンジニアになりたい理由の１つとも合致している

私が、エンジニアになりたい理由は、

大まかに、

・今まで、誰も作ったことないようなアプリを作りたいお
・大きな企業が実際に導入するような必要性が認められたアプリを作りたいお
・え、そんなアプリ作ったことあるの？と言われたいお

他にもあるが。


## もし可能であったら、最終的につけたい機能

**①全隊員が、各隊員のプロフィールを見れて、経験年数、レベル、周りの人からの評価、を閲覧できる**

**②隊員が、自分のプロフィール写真を登録できて、NFT化できる**

**③隊長は、隊長手当をもらう権利があるが、貰っていない人が多い（なので、投げ銭/寄付できる機能）**

**④現場の近くに、どこにトイレがあるか/どこに昼休憩で食べに行けるレストランがあるか、教えてくれる機能**

**⑤新入社員用に、警備業務の講義を配信できる機能**

**⑥法律と定款と就業規則と社内規則を閲覧できる機能**


# 簡潔に！！

## WHO/WHAT：誰のどんな課題を解決するのか？

私たち！

## WHY：なぜ、それを解決したいのか？

プライベートの時間が少なくなる！

## HOW：どうやって解決するのか？（サービス案）

DBに保存！


# 今後、どのように進めていくか

1. コア部分を作る
1. AWSに、デプロイ
1. 改善と機能追加
1. 斉藤様に使ってもらう
1. 改善と機能追加



#


## エレベータービッチ

<font color="MediumVioletRed">あ、高橋さん、お疲れ様です。</font>

<font color="SpringGreen">お、伊藤さん、お疲れ。</font>

<font color="MediumVioletRed">管制の人って、残業多いですか？</font>

<font color="SpringGreen">う〜ん、そこそこかな</font>

<font color="MediumVioletRed">255個もある現場を6人で回すって、大変そうですね</font>

<font color="SpringGreen">まあ、仕事だからね</font>

<font color="MediumVioletRed">そういば、最近僕、アプリ開発の勉強してるんですよ</font>

<font color="SpringGreen">そうなんだ。独学？</font>

<font color="MediumVioletRed">そうです！</font>

<font color="SpringGreen">えらいね！帰ってから、勉強までして</font>

<font color="MediumVioletRed">ありがとうございます。</font>

<font color="SpringGreen">・・・・</font>

<font color="MediumVioletRed">あ、で、えっと、ちょっと思いついたアプリがあって、</font>

<font color="SpringGreen">うん..</font>

<font color="MediumVioletRed">管制の人って、毎度、案件、コピペして隊員に送るの大変そうだなって思ったので、アプリから現場指示送るようにしたら、少しは作業量減りませんかね？</font>

<font color="SpringGreen">んー、どうだろ...アプリでそんなことできるのかな？</font>

<font color="MediumVioletRed">できると思いますよ！</font>

<font color="SpringGreen">へー</font>

<font color="MediumVioletRed">僕、勉強がてらに、簡単なアプリ、ちょっと作ってみますよ</font>

<font color="SpringGreen">おお、やる気がすごいね！笑</font>

<font color="MediumVioletRed">もし、出来上がったら、試作レベルで使ってもらえませんか？</font>

<font color="SpringGreen">とりあえず、わかりました。頑張って作ってみてください。楽しみにしています。</font>

<font color="MediumVioletRed">はい！ありがとうございます！</font>



**こうして、アプリ開発の旅が始まった。**


## オリジナルプロダクトのテーマ




```

「無駄な情報処理作業の手間を無く」 したい
「'自分'や'他の警備員'と'いつも私たちの現場を配慮しながら決めてくれている管制の方々'」 向けの
「S-Digital（略して、S-Degi(エスデジ)）」 は
「業務系アプリケーション」 です。

これは 「ユーザーの作業量と作業時間の短縮をする」 ことができ、
「システムを使っていないとき」 とは違って、
「大いに、時間が削減され、非常に利用価値」 がある。

```


# 希望

Webとモバイルの両方を作りたい

Webは、Next.js

モバイルは、ReactNative

で、6ヶ月後くらいに、完成させたい



## 手引き

[ブログ版](https://qiita.com/delsan/items/0cb9563f1f2490aa808d)

[S-Degiのメイン部分のみ/コア機能のみのGitHub](https://github.com/DiorJoker/S-Degital-Main-Core-Core)

[S-Degiのメイン部分のみ/コア機能のみの解説記事](https://qiita.com/delsan/items/745c26b6e614e91244f2)
