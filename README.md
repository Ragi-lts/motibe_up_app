# motibe_up_app
We are developing web applications to manage motive. 
The usage image is as follows.

- Set goals for the day every morning.
- Look back on yourself every night.

Only this.

## Set goals
We set goals with bullet points. 

## Look back on yourseld
Looking back is the most importtant feature of this app. Looking back weill be done according to the following two points.

- Set degree of achievement.
- Write a diary.

# memo
複数ユーザーが使う想定になっていない. 
ログイン機能やユーザー登録機能が必要. 

## メインメニュー
1段深い項目は、親項目に含む内容。つまり、「項目ごとに達成度を評価する」は、メインメニューで「日誌を完成させる」をクリックすることで実行することが出来る。
- 今日までの目標達成度が棒グラフ等(要検討)で確認できる
- 今日の日誌を作る
  - 箇条書きで目標を設定する
- 日誌を完成させる
  - 項目ごとに達成度を5段階で評価する
  - 一日の総評を文章で作成する(日記)
- これまでの日誌を確認する
  - 作成済みの日誌を一覧で確認する
- みんなの活動を見る
  - 公開された他のユーザーの日誌を見ることが出来る
  - 似たような活動をしているユーザーの日誌をみるために、日誌かユーザーにタグを付けるといいかも
  - コメント機能やいいね機能ででコミュニケーションを取れてもいいかも


## デザイン
[figma](https://www.figma.com/file/mWI9F1owr2AxObPEqLZH1R/motibe_up_app?node-id=0%3A1)

## データ構造
データベースにはDynamoDBのNoSQLデータベース使いたいなと思ってる.
ヘッドレスCMSとか使いたかったけど, 調べたら全然適した用途じゃなかったですね. 

- Diary
  - id: String
  - taskIds: String[]
  - tag: String[]
  - date: Date
- Task
  - id: String
  - title: String
  - comment: String
  - reviewId: String | Null
  - makeReview()
- Review
  - id: String
  - labelOfAchivement: Number
  - reflection: String
- User
  - id: String
  - name: String
  - profImg: String

ユーザーが今日の目標を設定すると同時にDiaryが生成され, 当日の目標であるTaskを1つ以上設定する. 
ユーザーはその日の終わりに当日のTaskに対してReviewを生成する. 
もしかしたら、達成度はTaskよりDiaryに置いて, 達成度とレビューを記入する形がいいのかもしれない. 

