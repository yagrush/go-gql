# golangでgithub GraphQL APIにクエリするサンプル。

## 外部OSSを使用せず、生のHttpRequestで実現する。

githubが公開しているgqlエンドポイント https://api.github.com/graphql に、

`cmd/main.go`
``` 
40行目:			"login": "yagrush",
```

で指定したgithubユーザーのname, emailを取ってくるクエリを投げる。

# このリポジトリのほかに必要なもの。

* golangのインストール。
* githubアカウント。
* Settings -> Developer settings -> Personal access tokens で発行したトークン。
   ->  read:user, user:email 権限を付与して発行してください。 
   -> sample.env を .env にリネームして、中の `GITHUB_TOKEN_GQL=` のうしろにトークンを書いて下さい。
* 指定したgithubユーザーがEメールを非公開に設定していると、空文字（""）しか取れません。（クエリ自体はエラーにはならない。）
* OSS github.com/joho/godotenv を使用しているので、お手元に無ければ`go get`してください。

# 実行

```
$ go run cmd/main.go

{"data":{"user":{"name":"yagrush","email":""}}}
$ 
```
