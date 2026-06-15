# SNS連携機能（Dashboard→SNS投稿）

## 情報ソース

| 資料名 | 種別 | 取得日 | 備考 |
|--------|------|--------|------|
| MEO Dashboard ヘルプセンター（help-meodash.zendesk.com） | 公式ヘルプ | 2026-06-12 | Claude in Chromeで直接参照 |

---

## SNS連携カテゴリの構成

| セクション | 内容 |
|-----------|------|
| SNS連携前にご確認ください | 運用フロー・投稿注意点・特定キーワード |
| Facebook・Instagram連携 | 各アカウント連携手順（10記事） |
| X（旧Twitter）連携 | アカウント連携・Developer Portal操作 |
| 投稿方法 | Dashboard→SNS+GBP同時投稿・削除反映（7記事） |
| Instagram分析機能 | ダッシュボード・競合分析・ファンユーザーリスト（12記事） |
| LINE連携 | LINE公式アカウント連携・メッセージ配信（9記事） |

⚠️ **SNS逆パターン（SNS→GBP）は `references/sns-reverse-integration.md` を参照。**

---

## Instagram連携（単体：Facebookを経由しない方法）

**前提：** Instagramアカウントのみで連携可能。ただし連携できるアカウントは**1つのみ**。

1. ビルアイコン→【設定】→【店舗】→連携を行う店舗をクリック
2. ページ下部の【Instagram連携】→【Instagramアカウント連携（単体）】をクリック
3. 【警告】が表示されるが新規連携の場合は【確認】を押す（現在連携済みのアカウントがある場合は既存連携が切れるので注意）
4. Instagramにログイン（セキュリティコードが届く場合あり）
5. 【許可する】を選択
6. DashboardのInstagram連携画面で連携アカウントが表示・「アクティブ」になっているか確認
7. 【連携対象】にチェックを入れて連携完了

⚠️ **【連携対象】にチェックを入れていない場合、投稿の取得はされない。**

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/31514282544921

---

## Instagram連携（Facebook経由）

**前提：** InstagramプロアカウントとFacebookビジネスページのリンクが必要。

1. 管理画面右上アイコン→【設定】→【店舗】→連携したい店舗を選択
2. ページ下部の【Instagram連携】→「＋Instagramアカウント追加」をクリック
3. 1店舗目：連携したいInstagramとリンクしているFacebookでログイン
   - 「現在および今後のページすべてにオプトイン」を選択→「続行」
   - 「現在および今後のInstagramアカウントすべてにオプトイン」を選択→「続行」
   - 「保存」をクリック
4. 2店舗目以降：「Reconnect」をクリック
5. 「OK」をクリック
6. ページ下部の【Instagram連携】で連携店舗のFacebookビジネスページの【連携対象】にチェック

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/5089164688409

---

## Facebook連携

1. 管理画面右上アイコン→【設定】→【店舗】→連携したい店舗を選択
2. ページ下部の【Facebook連携】→「＋Facebookアカウント追加」をクリック
3. 1店舗目：連携したいFacebookでログイン
   - 「現在および今後のページすべてにオプトイン」を選択→「続行」×2
   - 「保存」をクリック
4. 2店舗目以降：「Reconnect」をクリック
5. 「OK」をクリック
6. ページ下部の【Facebook連携】で連携店舗の【連携対象】にチェック

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/5089193980057

---

## X（旧Twitter）連携

### API制限と連携方式

2023年7月以降、X（旧Twitter）のAPIに制限がかかり、無料アカウントでは30日間のAPI利用によるGBP反映ポスト数が**全社共通で10,000通まで**に制限された。

| 連携方式 | 費用 | 特徴 |
|---------|------|------|
| **店舗共通API（無料版）** | 無料 | 全店舗共通のAPIキーを使用。月途中で10,000通超えると制限がかかる可能性あり |
| **店舗独自のAPI（有料版）** | 有料 | Twitter DeveloperアカウントのBasicプランを契約してAPIキーを発行。月途中制限が発生しにくい |

### X連携手順

1. Dashboardにログイン
2. 上部メニューから【店舗】を選択→Xを連携したい店舗を選択
3. 基本情報ページ下部の「Twitter連携」の「＋Twitterアカウント追加」をクリック
4. 連携方式を選択（無料：店舗共通API / 有料：店舗独自のAPI）
5. 右上の【X（旧Twitter）アカウント追加】を選択→TwitterアカウントのID・PWを入力
6. ダッシュボード画面に戻り「Twitter連携」欄にアカウント名が表示されたら完了

⚠️ **連携後の初期設定では（A）GBP投稿→Twitter反映、（B）Twitter投稿→GBP反映 の両方が有効になる。** TwitterをGBPに反映させたくない場合は「TW→GBP投稿」のチェックを外す。

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/5076012112921
**参照（API仕様）**：https://help-meodash.zendesk.com/hc/ja/articles/25222496698649

---

## Dashboard→SNS+GBP同時投稿

Dashboard上からSNS（X/Facebook/Instagram等）とGBPへ同時に投稿できる。

### 手順（イベント投稿の例）

1. 左ナビ【Googleデータ連携】→【Googleビジネスプロフィール】→【投稿】
2. 右上【新規作成】をクリック
3. 投稿タイプ：イベント を選択
4. 以下の項目を設定：
   - **②媒体**：投稿先のSNS媒体を選択（複数・全選択も可）
   - **③タイトル**：58文字以内
   - **④投稿日時**：即時または予約
   - **⑤開始・終了日時**
   - **⑥投稿内容**：1500文字以内
   - **⑦画像**
   - **⑧ボタン追加**（CTA）
   - **⑨ハッシュタグ**（半角#で入力）
5. 「登録する」をクリックして完了

### 各SNSの画像投稿制限

| 媒体 | 投稿可能枚数 |
|------|------------|
| Instagram | 1枚のみ |
| Facebook | 枚数制限なし |
| X（旧Twitter） | 最大4枚 |

⚠️ Xを選択した場合、イベント開催期間も投稿内容に含まれるため**全角140文字・半角280文字**の制限に注意。
⚠️ Instagramを選択した場合、画像を選択しないと投稿されない。
⚠️ SNS側から2枚以上の画像入り投稿をGBPに反映する場合、**1枚目の写真のみ**がGBPに反映される。

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/5149798275353

---

## LINE連携

### 連携手順

**事前準備：** LINE Developersで以下を準備する
- チャネルID
- チャネルシークレット
- あなたのユーザーID
- チャネルアクセストークン

1. Dashboard TOPページ右上アイコン→【設定】→【店舗】
2. 連携させたい店舗名をクリック
3. 詳細ページ中央の「LINE連携」の4つの入力欄に移動
4. 準備した「チャネルID」「チャネルシークレット」「ユーザーID」「チャネルアクセストークン」を入力
5. 画面下部の【登録する】をクリックして完了

**参照**：https://help-meodash.zendesk.com/hc/ja/articles/10075930984217
**参照（事前準備）**：https://help-meodash.zendesk.com/hc/ja/articles/13639501298969
**参照（LINE Webhook URL設定）**：https://help-meodash.zendesk.com/hc/ja/articles/44131495422361
**参照（メッセージ配信）**：https://help-meodash.zendesk.com/hc/ja/articles/37312392430873

---

## SNS投稿に関する注意事項

**参照（投稿注意点）**：https://help-meodash.zendesk.com/hc/ja/articles/5245459826073
**参照（特定キーワード）**：https://help-meodash.zendesk.com/hc/ja/articles/21348670942105
**参照（運用フロー）**：https://help-meodash.zendesk.com/hc/ja/articles/32446053499801
