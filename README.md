# Create IT term test paper

研修における用語テスト問題生成ツール。
別ファイルである dicts.py に定義した用語からピックアップして問題を作成する。
slackワークスペースの指定チャンネルに、生成した問題用紙をアップロードする。
対象の用語 (10語) はランダムで選択される。



## アプリ構成

```txt
createI3TPaper ┳ createI3TPaper_main.py
               ┣ dicts.py
               ┣ env.py
               ┣ paths.py
               ┣ template ┳ template_1st.md
               ┃          ┗ template_2nd.md
               ┗ exam_papers ┳ IT用語テスト_yyyymmdd_name.md
                              ┣ ...
```



## 実行方法

env.py に OAuth Access Token (Bot用) の入力、および Slack チャンネルIDの入力を行った上で、当ツールが格納されているディレクトリにて以下を実行する。

```bash
python createI3TPaper_main.py
```



##  TODO

- [ ] 外部ファイルへの書き出し処理に、アップロード処理が入るのが汚いので修正
- [ ] slack API を使用しての、ファイルアップロード処理の実装修正
    - 削除機能の追加（アップロードの際に、既に本日分がアップロードされていたら削除してから上げる処理）
- [ ] 出題される用語は毎回重複する可能性があるため、履歴を保持して数回前までに選択された用語を除外するよう修正



## 注意事項

- Bot用の API token は App ディレクトリ から Bots を作成して、Botsの管理画面から取得する
- Channelをブラウザで開いて、https://xxx.slack.com/messages/{ChannelID} が Chennel ID 。
- Private Channel に投稿したい時は、Bot をその Channel に /invite するのを忘れずに。

---

## IT用語テストの必要性

このテストはIT業界未経験の方を対象とする。解答制限時間は20分ほど。採点は個別に実施する。

### 現場には多種多様な業界用語が存在しており、その定義は調べないと理解できないことが多い。  

皆が何となく使っている言葉はそのまま調べずに雰囲気で済ませることがあるが、ドメインに関わる用語であれば意味の取り違いは許されない。
しっかりと調べることを癖付ける為にIT用語テストを実施する。


### 始めは分からなくても時間内に調査してレポートを作成するということは業務的にあり得る。  

時間内に形にする訓練でもある。


### 仕事において文章の作成能力は重要である。

たまに相手の発信する内容がこちら側に伝わってこない状況に遭遇することがあるが、これは相手とこちらがそれぞれ持っている情報に差があることから発生する。これを改善するには伝える内容に過不足がないか、また言葉の定義などについて認識がズレていないかを意識する必要がある。
このテストを機に自身の文章構成を客観的に見直してもらう。チェックポイントとして、以下が挙げられる。  

- 情報が欠落していないか : 正しい情報を文章化すること
- 情報過多になっていないか : 伝えたいことがまとまっているかを意識する
- その用語の使い方は正しいか : 用語の定義が異なることによって生じる認識のズレは悲惨であるため要確認！


