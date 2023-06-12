# 検索広告操作履歴
1. [操作履歴フィールド](#anchor1)
2. [有効エンティティ名](#anchor2)
3. [有効イベントタイプ](#anchor3)
4. [各エンティティの出力項目名](#anchor4)
5. [カラム](#anchor5)

## 項目
操作履歴の項目は下記の通りです。※2020年08月28日時点のデータです。

#### 1. 操作履歴フィールド
<a id="anchor1"></a>

|項目（日本語）|
|---|
|日時|
|操作した利用者|
|ソースタイプ|
|アカウント名|
|アカウントID|
|キャンペーン名|
|キャンペーンID|
|広告グループ名|
|広告グループID|
|広告名|
|広告ID|
|広告タイプ|
|キーワード|
|キーワードID|
|データ自動挿入リストID|
|ページフィードID|
|広告表示オプションID|
|自動入札ID|
|ターゲットリスト名|
|ターゲットリストID|
|ページフィードターゲティングID|
|コンバージョン設定ID|
|対象外キーワードリストID|
|ラベルID|
|ラベル名|
|エンティティ|
|イベントタイプ|
|項目|
|更新前|
|更新後|

#### 2.有効エンティティ名
<a id="anchor2"></a>

|エンティティタイプ|項目（日本語）|
|---|---|
|CAMPAIGN|キャンペーン|
|NEGATIVE_CAMPAIGN_CRITERION|キャンペーン対象外キーワード|
|CAMPAIGN_CRITERION|キャンペーンターゲティング|
|AD_GROUP|広告グループ|
|AD_GROUP_BID_MULTIPLIER|広告グループ|
|BIDDABLE_AD_GROUP_CRITERION|キーワード|
|NEGATIVE_AD_GROUP_CRITERION|広告グループ対象外キーワード|
|AD|広告|
|FEED|フィード|
|FEED_ITEM|広告表示オプション|
|SS_IO|アカウント|
|SS_CONVERSION|コンバージョン測定|
|CAMPAIGN_FEED|広告表示オプション|
|AD_GROUP_FEED|広告表示オプション|

#### 3.有効イベントタイプ
<table id= 'anchor3'>
<tr>
 <th>エンティティタイプ</th>
 <th>項目（日本語）</th>
</tr>

<tr><td rowspan='4'>CAMPAIGN</td><td>キャンペーン設定情報変更</td></tr>
<tr><td>配信設定変更</td></tr>
<tr><td>追加</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='3'>CAMPAIGN_CRITERION</td><td>追加</td></tr>
<tr><td>入札価格調整率変更</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='2'>NEGATIVE_CAMPAIGN_CRITERION</td><td>追加</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='5'>AD_GROUP</td><td>広告グループ設定情報変更</td></tr>
<tr><td>配信設定変更</td></tr>
<tr><td>広告グループ入札価格設定</td></tr>
<tr><td>追加</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='3'>AD_GROUP_BID_MULTIPLIER</td><td>追加</td></tr>
<tr><td>広告グループ設定情報変更</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='6'>BIDDABLE_AD_GROUP_CRITERION</td><td>キーワード設定変更</td></tr>
<tr><td>キーワード審査</td></tr>
<tr><td>配信設定変更</td></tr>
<tr><td>キーワード入札価格設定</td></tr>
<tr><td>追加</td></tr>
<tr><td>削除</td></tr>
<tr><td rowspan='2'>NEGATIVE_AD_GROUP_CRITERION</td><td>対象外キーワード追加（広告グループ）</td></tr>
<tr><td>対象外キーワード削除（広告グループ）</td></tr>
<tr><td rowspan='5'>AD</td><td>追加</td></tr>
<tr><td>広告設定変更</td></tr>
<tr><td>広告削除</td></tr>
<tr><td>広告審査</td></tr>
<tr><td>配信設定変更</td></tr>

</table>

#### 4.各エンティティの出力項目名
<table id="anchor4">
<tr>
 <th>エンティティタイプ</th>
 <th>項目（日本語）</th>
</tr>
 
<tr><td rowspan='35'>CAMPAIGN</td><td>キャンペーン名</td></tr>
<tr><td>配信設定</td></tr>
<tr><td>開始日</td></tr>
<tr><td>終了日</td></tr>
<tr><td>広告表示の最適化</td></tr>
<tr><td>キャンペーン予算（日額）</td></tr>
<tr><td>配信方法</td></tr>
<tr><td>入札方法</td></tr>
<tr><td>入札価格の上限</td></tr>
<tr><td>地域判定の詳細設定</td></tr>
<tr><td>除外地域判定の詳細設定</td></tr>
<tr><td>入札価格調整率（%）</td></tr>
<tr><td>ポートフォリオ入札設定</td></tr>
<tr><td>キャンペーンタイプ</td></tr>
<tr><td>OS</td></tr>
<tr><td>アプリID/パッケージ名</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>カスタムパラメータキー1</td></tr>
<tr><td>カスタムパラメータキー2</td></tr>
<tr><td>カスタムパラメータキー3</td></tr>
<tr><td>カスタムパラメータ値1</td></tr>
<tr><td>カスタムパラメータ値2</td></tr>
<tr><td>カスタムパラメータ値3</td></tr>
<tr><td>ページフィードID</td></tr>
<tr><td>配信対象ユーザー</td></tr>
<tr><td>拡張クリック単価設定</td></tr>
<tr><td>広告費用対効果の目標値</td></tr>
<tr><td>入札価格の上限（広告費用対効果の目標値）</td></tr>
<tr><td>入札価格の下限（広告費用対効果の目標値）</td></tr>
<tr><td>入札価格の上限（クリック数の最大化）</td></tr>
<tr><td>目標予算（日額）</td></tr>
<tr><td>コンバージョン単価の目標値</td></tr>
<tr><td>入札価格の上限（コンバージョン単価の目標値）</td></tr>
<tr><td>入札価格の下限（コンバージョン単価の目標値）</td></tr>
<tr><td>対象の指定方法</td></tr>
<tr><td rowspan='4'>CAMPAIGN_CRITERION</td><td>地域</td></tr>
<tr><td>曜日・時間帯</td></tr>
<tr><td>デバイス</td></tr>
<tr><td>広告掲載方式の指定</td></tr>
<tr><td rowspan='2'>NEGATIVE_CAMPAIGN_CRITERION</td><td>対象外キーワード</td></tr>
<tr><td>マッチタイプ</td></tr>
<tr><td rowspan='14'>AD_GROUP</td><td>広告グループ名</td></tr>
<tr><td>配信設定</td></tr>
<tr><td>広告グループ入札価格</td></tr>
<tr><td>ポートフォリオ入札設定</td></tr>
<tr><td>自動入札タイプ</td></tr>
<tr><td>配信対象ユーザー</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>カスタムパラメータキー1</td></tr>
<tr><td>カスタムパラメータキー2</td></tr>
<tr><td>カスタムパラメータキー3</td></tr>
<tr><td>カスタムパラメータ値1</td></tr>
<tr><td>カスタムパラメータ値2</td></tr>
<tr><td>カスタムパラメータ値3</td></tr>
<tr><td>広告表示の最適化</td></tr>
<tr><td rowspan='1'>AD_GROUP_BID_MULTIPLIER</td><td>入札価格調整率（%）</td></tr>
<tr><td rowspan='19'>BIDDABLE_AD_GROUP_CRITERION</td><td>キーワード</td></tr>
<tr><td>マッチタイプ</td></tr>
<tr><td>配信設定</td></tr>
<tr><td>現在設定中のカスタムURL</td></tr>
<tr><td>審査状況</td></tr>
<tr><td>入札価格</td></tr>
<tr><td>審査完了日</td></tr>
<tr><td>ポートフォリオ入札設定</td></tr>
<tr><td>自動入札タイプ</td></tr>
<tr><td>最終リンク先URL</td></tr>
<tr><td>スマートフォン向けURL</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>カスタムパラメータキー1</td></tr>
<tr><td>カスタムパラメータキー2</td></tr>
<tr><td>カスタムパラメータキー3</td></tr>
<tr><td>カスタムパラメータ値1</td></tr>
<tr><td>カスタムパラメータ値2</td></tr>
<tr><td>カスタムパラメータ値3</td></tr>
<tr><td>制限ステータス</td></tr>
<tr><td rowspan='2'>NEGATIVE_AD_GROUP_CRITERION</td><td>対象外キーワード</td></tr>
<tr><td>マッチタイプ</td></tr>
<tr><td rowspan='20'>AD</td><td>広告名</td></tr>
<tr><td>広告タイプ</td></tr>
<tr><td>優先配信デバイス設定</td></tr>
<tr><td>配信設定</td></tr>
<tr><td>タイトル</td></tr>
<tr><td>タイトル2</td></tr>
<tr><td>説明文1</td></tr>
<tr><td>説明文2</td></tr>
<tr><td>リンク先URL</td></tr>
<tr><td>表示URL</td></tr>
<tr><td>ディレクトリ1</td></tr>
<tr><td>ディレクトリ2</td></tr>
<tr><td>OS</td></tr>
<tr><td>アプリID/パッケージ名</td></tr>
<tr><td>審査状況</td></tr>
<tr><td>最終リンク先URL</td></tr>
<tr><td>スマートフォン向けURL</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>審査完了日</td></tr>
<tr><td>制限ステータス</td></tr>
<tr><td rowspan='22'>FEED</td><td>フィードID</td></tr>
<tr><td>フィード名</td></tr>
<tr><td>フィード属性1</td></tr>
<tr><td>フィード属性2</td></tr>
<tr><td>フィード属性3</td></tr>
<tr><td>フィード属性4</td></tr>
<tr><td>フィード属性5</td></tr>
<tr><td>フィード属性6</td></tr>
<tr><td>フィード属性7</td></tr>
<tr><td>フィード属性8</td></tr>
<tr><td>フィード属性9</td></tr>
<tr><td>フィード属性10</td></tr>
<tr><td>フィード属性11</td></tr>
<tr><td>フィード属性12</td></tr>
<tr><td>フィード属性13</td></tr>
<tr><td>フィード属性14</td></tr>
<tr><td>フィード属性15</td></tr>
<tr><td>フィード属性16</td></tr>
<tr><td>フィード属性17</td></tr>
<tr><td>フィード属性18</td></tr>
<tr><td>フィード属性19</td></tr>
<tr><td>フィード属性20</td></tr>
<tr><td rowspan='53'>FEED_ITEM</td><td>地域</td></tr>
<tr><td>審査状況</td></tr>
<tr><td>審査完了日</td></tr>
<tr><td>広告表示オプションID</td></tr>
<tr><td>キャンペーンID</td></tr>
<tr><td>広告グループID</td></tr>
<tr><td>キーワード</td></tr>
<tr><td>マッチタイプ</td></tr>
<tr><td>クイックリンクテキスト</td></tr>
<tr><td>クイックリンクURL</td></tr>
<tr><td>クイックリンク説明文1</td></tr>
<tr><td>クイックリンク説明文2</td></tr>
<tr><td>電話番号</td></tr>
<tr><td>クイックリンクテキスト（画像）</td></tr>
<tr><td>クイックリンクURL（画像）</td></tr>
<tr><td>メディアID</td></tr>
<tr><td>テキスト補足テキスト</td></tr>
<tr><td>テキスト補足テキストヘッダ</td></tr>
<tr><td>テキスト補足テキスト値</td></tr>
<tr><td>優先配信デバイス設定</td></tr>
<tr><td>開始日</td></tr>
<tr><td>終了日</td></tr>
<tr><td>曜日・時間帯</td></tr>
<tr><td>最終リンク先URL</td></tr>
<tr><td>スマートフォン向けURL</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>カスタムパラメータキー1</td></tr>
<tr><td>カスタムパラメータキー2</td></tr>
<tr><td>カスタムパラメータキー3</td></tr>
<tr><td>カスタムパラメータ値1</td></tr>
<tr><td>カスタムパラメータ値2</td></tr>
<tr><td>カスタムパラメータ値3</td></tr>
<tr><td>データ自動挿入リスト1</td></tr>
<tr><td>データ自動挿入リスト2</td></tr>
<tr><td>データ自動挿入リスト3</td></tr>
<tr><td>データ自動挿入リスト4</td></tr>
<tr><td>データ自動挿入リスト5</td></tr>
<tr><td>データ自動挿入リスト6</td></tr>
<tr><td>データ自動挿入リスト7</td></tr>
<tr><td>データ自動挿入リスト8</td></tr>
<tr><td>データ自動挿入リスト9</td></tr>
<tr><td>データ自動挿入リスト10</td></tr>
<tr><td>データ自動挿入リスト11</td></tr>
<tr><td>データ自動挿入リスト12</td></tr>
<tr><td>データ自動挿入リスト13</td></tr>
<tr><td>データ自動挿入リスト14</td></tr>
<tr><td>データ自動挿入リスト15</td></tr>
<tr><td>データ自動挿入リスト16</td></tr>
<tr><td>データ自動挿入リスト17</td></tr>
<tr><td>データ自動挿入リスト18</td></tr>
<tr><td>データ自動挿入リスト19</td></tr>
<tr><td>データ自動挿入リスト20</td></tr>
<tr><td>制限ステータス</td></tr>
<tr><td rowspan='18'>SS_IO</td><td>アカウント名</td></tr>
<tr><td>アカウント予算</td></tr>
<tr><td>代理店担当者名</td></tr>
<tr><td>代理店の所在地域</td></tr>
<tr><td>広告主の所在地域</td></tr>
<tr><td>アカウント作成日</td></tr>
<tr><td>掲載終了日</td></tr>
<tr><td>担当者名（広告主）</td></tr>
<tr><td>自動入金額</td></tr>
<tr><td>自動入金設定</td></tr>
<tr><td>自動入金用クレジットカード登録者のYahoo! JAPANビジネスID</td></tr>
<tr><td>適用プロモーションコード</td></tr>
<tr><td>配信設定</td></tr>
<tr><td>ヤフーによる配信設定</td></tr>
<tr><td>連絡先利用者のYahoo! JAPANビジネスID</td></tr>
<tr><td>トラッキングURL</td></tr>
<tr><td>自動タグ設定</td></tr>
<tr><td rowspan='13'>SS_CONVERSION</td><td>コンバージョン名</td></tr>
<tr><td>コンバージョン種別</td></tr>
<tr><td>コンバージョン測定の目的</td></tr>
<tr><td>ステータス</td></tr>
<tr><td>計測方法</td></tr>
<tr><td>自動入札への利用</td></tr>
<tr><td>計測期間</td></tr>
<tr><td>1コンバージョンあたりの価値</td></tr>
<tr><td>OS</td></tr>
<tr><td>測定タイミング</td></tr>
<tr><td>パッケージ名</td></tr>
<tr><td>ポストバックURL</td></tr>
<tr><td>デバイスをまたいだコンバージョンの測定</td></tr>
<tr><td rowspan='2'>CAMPAIGN_FEED</td><td>キャンペーン関連付け</td></tr>
<tr><td>デバイス</td></tr>
<tr><td rowspan='2'>AD_GROUP_FEED</td><td>広告グループ関連付け</td></tr>
<tr><td>デバイス</td></tr>

</table>

#### 5.カラム
<table id="anchor5">
<tr>
 <th>項目（日本語）</th>
 <th>値</th>
</tr>

<tr><td rowspan='6'>広告表示の最適化</td><td>最適化して配信（クリック率の高い広告を優先的に配信）</td></tr>
<tr><td>均等に配信（90日間均等に配信、その後最適化）</td></tr>
<tr><td>無期限で均等に配信（最適化しない）</td></tr>
<tr><td>最適化して配信（コンバージョンが期待できる広告を優先的に配信）</td></tr>
<tr><td>最適化して配信</td></tr>
<tr><td>最適化しない</td></tr>
<tr><td rowspan='6'>広告タイプ</td><td>テキスト（15・33）</td></tr>
<tr><td>テキスト（15・19-19）</td></tr>
<tr><td>ショートテキスト（12・12）</td></tr>
<tr><td>アプリ（12・17-17）</td></tr>
<tr><td>テキスト（15-15・40）</td></tr>
<tr><td>動的検索連動型広告</td></tr>
<tr><td rowspan='5'>審査状況</td><td>承認</td></tr>
<tr><td>審査中</td></tr>
<tr><td>掲載不可</td></tr>
<tr><td>掲載停止</td></tr>
<tr><td>編集内容審査中</td></tr>
<tr><td rowspan='7'>自動入札タイプ</td><td>自動</td></tr>
<tr><td>個別クリック単価</td></tr>
<tr><td>検索結果ページの目標掲載位置</td></tr>
<tr><td>広告費用対効果の目標値</td></tr>
<tr><td>クリック数の最大化</td></tr>
<tr><td>コンバージョン数の最大化</td></tr>
<tr><td>コンバージョン単価の目標値</td></tr>
<tr><td rowspan='2'>配信方法</td><td>設定あり</td></tr>
<tr><td>設定なし</td></tr>
<tr><td rowspan='3'>デバイス</td><td>PC・タブレット</td></tr>
<tr><td>スマートフォン</td></tr>
<tr><td>すべて</td></tr>
<tr><td rowspan='3'>対象の指定方法</td><td>ページフィード</td></tr>
<tr><td>ドメイン全体</td></tr>
<tr><td>ドメイン全体とページフィードを併用</td></tr>
<tr><td rowspan='3'>マッチタイプ</td><td>部分一致</td></tr>
<tr><td>フレーズ一致</td></tr>
<tr><td>完全一致</td></tr>
<tr><td rowspan='2'>配信設定</td><td>オン</td></tr>
<tr><td>オフ</td></tr>
<tr><td rowspan='2'>広告グループ関連付け</td><td>オン</td></tr>
<tr><td>オフ</td></tr>
<tr><td rowspan='2'>配信対象ユーザー</td><td>全ユーザー</td></tr>
<tr><td>ターゲットリストのユーザー</td></tr>
<tr><td rowspan='4'>ターゲットリスト種別</td><td>デフォルトターゲットリスト</td></tr>
<tr><td>条件ターゲットリスト</td></tr>
<tr><td>組み合わせターゲットリスト</td></tr>
<tr><td>カスタムターゲットリスト</td></tr>
<tr><td rowspan='2'>リーチ蓄積ステータス</td><td>有効</td></tr>
<tr><td>無効</td></tr>
<tr><td rowspan='2'>ターゲットリスト所有者</td><td>所有者</td></tr>
<tr><td>共有</td></tr>
<tr><td rowspan='2'>ターゲットリスト共有</td><td>共有不可</td></tr>
<tr><td>共有可</td></tr>
<tr><td rowspan='3'>キャンペーンタイプ</td><td>標準キャンペーン</td></tr>
<tr><td>アプリダウンロードキャンペーン</td></tr>
<tr><td>動的検索連動型広告キャンペーン</td></tr>
<tr><td rowspan='2'>OS</td><td>iOS</td></tr>
<tr><td>Android</td></tr>
<tr><td rowspan='2'>訪問者</td><td>すべて</td></tr>
<tr><td>限定</td></tr>
<tr><td rowspan='2'>期間付き条件付きターゲットリスト</td><td>期間指定あり</td></tr>
<tr><td>期間指定なし</td></tr>
<tr><td rowspan='49'>代理店の所在地域</td><td>北海道</td></tr>
<tr><td>青森</td></tr>
<tr><td>岩手</td></tr>
<tr><td>宮城</td></tr>
<tr><td>秋田</td></tr>
<tr><td>山形</td></tr>
<tr><td>福島</td></tr>
<tr><td>茨城</td></tr>
<tr><td>栃木</td></tr>
<tr><td>群馬</td></tr>
<tr><td>埼玉</td></tr>
<tr><td>千葉</td></tr>
<tr><td>東京</td></tr>
<tr><td>神奈川</td></tr>
<tr><td>新潟</td></tr>
<tr><td>富山</td></tr>
<tr><td>石川</td></tr>
<tr><td>福井</td></tr>
<tr><td>山梨</td></tr>
<tr><td>長野</td></tr>
<tr><td>岐阜</td></tr>
<tr><td>静岡</td></tr>
<tr><td>愛知</td></tr>
<tr><td>三重</td></tr>
<tr><td>滋賀</td></tr>
<tr><td>京都</td></tr>
<tr><td>大阪</td></tr>
<tr><td>兵庫</td></tr>
<tr><td>奈良</td></tr>
<tr><td>和歌山</td></tr>
<tr><td>鳥取</td></tr>
<tr><td>島根</td></tr>
<tr><td>岡山</td></tr>
<tr><td>広島</td></tr>
<tr><td>山口</td></tr>
<tr><td>徳島</td></tr>
<tr><td>香川</td></tr>
<tr><td>愛媛</td></tr>
<tr><td>高知</td></tr>
<tr><td>福岡</td></tr>
<tr><td>佐賀</td></tr>
<tr><td>長崎</td></tr>
<tr><td>熊本</td></tr>
<tr><td>大分</td></tr>
<tr><td>宮崎</td></tr>
<tr><td>鹿児島</td></tr>
<tr><td>沖縄</td></tr>
<tr><td>海外</td></tr>
<tr><td>未設定</td></tr>
<tr><td rowspan='49'>広告主の所在地域</td><td>北海道</td></tr>
<tr><td>青森</td></tr>
<tr><td>岩手</td></tr>
<tr><td>宮城</td></tr>
<tr><td>秋田</td></tr>
<tr><td>山形</td></tr>
<tr><td>福島</td></tr>
<tr><td>茨城</td></tr>
<tr><td>栃木</td></tr>
<tr><td>群馬</td></tr>
<tr><td>埼玉</td></tr>
<tr><td>千葉</td></tr>
<tr><td>東京</td></tr>
<tr><td>神奈川</td></tr>
<tr><td>新潟</td></tr>
<tr><td>富山</td></tr>
<tr><td>石川</td></tr>
<tr><td>福井</td></tr>
<tr><td>山梨</td></tr>
<tr><td>長野</td></tr>
<tr><td>岐阜</td></tr>
<tr><td>静岡</td></tr>
<tr><td>愛知</td></tr>
<tr><td>三重</td></tr>
<tr><td>滋賀</td></tr>
<tr><td>京都</td></tr>
<tr><td>大阪</td></tr>
<tr><td>兵庫</td></tr>
<tr><td>奈良</td></tr>
<tr><td>和歌山</td></tr>
<tr><td>鳥取</td></tr>
<tr><td>島根</td></tr>
<tr><td>岡山</td></tr>
<tr><td>広島</td></tr>
<tr><td>山口</td></tr>
<tr><td>徳島</td></tr>
<tr><td>香川</td></tr>
<tr><td>愛媛</td></tr>
<tr><td>高知</td></tr>
<tr><td>福岡</td></tr>
<tr><td>佐賀</td></tr>
<tr><td>長崎</td></tr>
<tr><td>熊本</td></tr>
<tr><td>大分</td></tr>
<tr><td>宮崎</td></tr>
<tr><td>鹿児島</td></tr>
<tr><td>沖縄</td></tr>
<tr><td>海外</td></tr>
<tr><td>未設定</td></tr>
<tr><td rowspan='2'>自動入金設定</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>ヤフーによる配信設定</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>参照権限</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>登録更新権限</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>管理者権限</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>効果測定に関するお知らせ</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>審査関連のお知らせ</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>料金に関するお知らせ</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>有効フラグ</td><td>オフ</td></tr>
<tr><td>オン</td></tr>
<tr><td rowspan='2'>ステータス</td><td>オン</td></tr>
<tr><td>オフ</td></tr>
<tr><td rowspan='5'>コンバージョン測定の目的</td><td>その他</td></tr>
<tr><td>主要なページの閲覧</td></tr>
<tr><td>購入/販売</td></tr>
<tr><td>お申し込み</td></tr>
<tr><td>販売促進</td></tr>
<tr><td rowspan='4'>当該ページの形式</td><td>html</td></tr>
<tr><td>chtml</td></tr>
<tr><td>xhtml (モバイル)</td></tr>
<tr><td>wml</td></tr>
<tr><td rowspan='2'>該当ページのセキュリティレベル</td><td>HTTP</td></tr>
<tr><td>HTTPS</td></tr>
<tr><td rowspan='4'>コンバージョン種別</td><td>ウェブページ</td></tr>
<tr><td>電話発信</td></tr>
<tr><td>アプリ</td></tr>
<tr><td>インポート</td></tr>
<tr><td rowspan='2'>計測方法</td><td>毎回</td></tr>
<tr><td>初回のみ</td></tr>
<tr><td rowspan='2'>自動入札への利用</td><td>する</td></tr>
<tr><td>しない</td></tr>
<tr><td rowspan='3'>測定タイミング</td><td>アプリのダウンロード</td></tr>
<tr><td>アプリの初回起動</td></tr>
<tr><td>アプリ内のユーザー行動</td></tr>
<tr><td rowspan='2'>インタレストマッチの配信設定</td><td>オン</td></tr>
<tr><td>オフ</td></tr>
<tr><td rowspan='3'>地域判定の詳細設定</td><td>ユーザーの所在地</td></tr>
<tr><td>検索キーワードに含まれる地域、ユーザーが関心を示している地域</td></tr>
<tr><td>ユーザーの所在地、検索キーワードに含まれる地域、ユーザーが関心を示している地域</td></tr>
<tr><td rowspan='2'>除外地域判定の詳細設定</td><td>ユーザーの所在地</td></tr>
<tr><td>ユーザーの所在地、検索キーワードに含まれる地域、ユーザーが関心を示している地域</td></tr>
<tr><td rowspan='1'>優先配信デバイス設定</td><td>スマートフォン</td></tr>
<tr><td rowspan='2'>掲載位置（検索結果ページの目標掲載位置）</td><td>1ページ目</td></tr>
<tr><td>1ページ目上部</td></tr>
<tr><td rowspan='2'>入札調整方法（検索結果ページの目標掲載位置）</td><td>手動で入札価格を設定</td></tr>
<tr><td>完全に自動化</td></tr>
<tr><td rowspan='2'>予算による制限（検索結果ページの目標掲載位置）</td><td>引き上げる</td></tr>
<tr><td>引き上げない</td></tr>
<tr><td rowspan='2'>品質が低いキーワード（検索結果ページの目標掲載位置）</td><td>引き上げる</td></tr>
<tr><td>引き上げない</td></tr>

</table>
