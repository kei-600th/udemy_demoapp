FROM ruby:2.7.2-alpine

# Dockerfile内で使用する変数を定義
ARG WORKDIR
ARG RUNTIME_PACKAGES="nodejs tzdata postgresql-dev postgresql git"
ARG DEV_PACKAGES="build-base curl-dev" 

#環境変数を定義(Dockerfile,コンテナ参照可)
ENV HOME=/${WORKDIR} \
    LANG=C.UTF-8 \
    TZ=Asia/Tokyo

# ENV test（このRUN命令は確認のためなので無くても良い）
# ベースイメージに対してコマンドを実行する

#Dockerfile内で指定した命令を実行する 
#作業ディレクトリを定義
# コンテナ/app/Railsアプリ
WORKDIR ${HOME}

# ホスト側(PC)のファイルをコンテナにコピー(Dockerfileがあるディレクトリ以下のみ)
COPY Gemfile* ./

# apk ...Alpine Linuxのコマンド
# apk update = パッケージの最新リストを取得
RUN apk update && \
# apk upgrade = インストールパッケージを最新のものに
    apk upgrade && \
    #apk add = パッケージのインストールを実行
    # --nocache = パッケージをキャッシュしない(Dockerイメージを軽量化)
    apk add --no-cache ${RUNTIME_PACKAGES} && \
    # --virtual　名前(任意) = 仮装パッケージ
    apk add --virtual build-dependencies --no-cache ${DEV_PACKAGES} && \
    # Gemのインストールコマンド
    # -j4 = Gemインストールの高速化
    bundle install -j4 && \
    # パッケージを削除(Dockerイメージの軽量化)
    apk del build-dependencies

# Dockerfileがあるディレクトリ全てのファイル
COPY . ./

# コンテナ内で実行したいコマンドを定義
# -b バインド プロセスを指定したip(0.0.0.0)アドレスに紐付け(バインド)する
CMD ["rails", "server", "-b", "0.0.0.0"]