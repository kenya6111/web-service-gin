# 注意 go.mod記載のversionと合わせる
# 軽量にするためalpineを使用
FROM golang:tip-alpine3.22 AS dev

# コンテナ内の作業ディレクトリを/appに設定
WORKDIR /go/src

# ホストマシンからtodo-app内の全ファイルを、コンテナ内の作業ディレクトリ(/app)にコピー
COPY . .

RUN go install github.com/air-verse/air@latest

# go.modファイルに記載された依存パッケージをdownload
RUN go mod download

# main.goファイルをコンパイルして、実行ファイルを作成
RUN go build -o main ./main.go

# コンテナの8080ポートを公開
# EXPOSE 8080

# コンテナ起動後に、実行ファイルを実行
# CMD ["./main"]
CMD ["air", "-c", ".air.toml"]


FROM alpine:3.22.1 AS prod

WORKDIR /app

COPY --from=dev /go/src/main .

COPY . .

CMD [ "/app/main" ]