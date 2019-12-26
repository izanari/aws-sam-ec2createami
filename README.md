# AMIバックアップを自動取得するLambdaファンクション
元のコードは、[AMIバックアップを取るLambdaファンクション（python）](https://qiita.com/Hiroyama-Yutaka/items/9fab02438dc22c0b85ea)にある[Yutaka Hiroyama](https://qiita.com/Hiroyama-Yutaka)さんのコードです。

## 元のコードからの変更点
- Python3.8で動作するように以下を変更
  - `dict.has_key`を`dict.get`に変更
  - print 'str'をprint(str)に変更
- create_image時のreboot判断を、タグから取得するように処理を追加

## 環境
- Python3.8
- SAM CLI, version 0.39.0

## Backupを取得する時間
- 日本時間の2:15に処理が開始するようにしています。この時間を変更したい場合は、template.yamlの以下の行を変更してください。
  - `Schedule: cron(15 19 * * ? *)` 
  - 
## デプロイ方法
```
sam package --s3-bucket yourbacket
sam deploy --guided
```
- ２回め以降は`sam deploy`のままでもOK