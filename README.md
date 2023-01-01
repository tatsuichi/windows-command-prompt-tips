## WindowsコマンドプロンプトTips集

## 実行環境

+ Windows10 64bit
+ cmd.exe

### 起動方法
1. Winキー + R
1. "cmd"と入力する
1. Enterキー 

または

1. Winキー
1. "コマンドプロンプト"と入力する
1. Enterキー

### バッチファイル
##### ファイルの先頭に記載する定型文
```bat
@echo off
cd /d %~dp0
```
#### バッチを即時終了させない
ファイルの最後で入力待ちさせる
```bat
pause
```
##### コメント(アウト)
```bat
rem コメント
```
##### ログ出力
```bat
コマンド >> ログファイル > 2>&1
```
##### 変数に設定する
=の前後にスペースがないこと
```bat
rem OK
set 変数=値
rem NG
set 変数 = 値
```
##### 変数を扱う
%で括る
```bat
echo %変数%
```
##### 年月日時分秒
```bat
set year=%date:~0,4%
set month=%date:~5,2%
set day=%date:~8,2%
set hour=%time:~0,2%
set min=%time:~3,2%
set sec=%time:~6,2%

echo %year%
echo %month%
echo %day%
echo %hour%
echo %min%
echo %sec%
```
##### 戻り値
```bat
echo %ERRORLEVEL%

if %ERRORLEVEL% equ 0 (
    REM 正常処理
) else (
    REM 異常処理
)
```

### コマンド関連
##### ヘルプ表示
```bat
コマンド /?
または
コマンド --help
```
##### 移動
```bat
cd 移動先のパス
```
##### ファイルの全行数カウント
```bat
find /v /c "" *.*
```
##### フォルダ構成の表示
```bat
tree
```
##### 文字コード
```bat
rem Shift-JIS
chcp 932
rem UTF-8
chcp 65001
```
##### IPアドレス等の確認
```bat
ipconfig /all
```
##### ネットワークの疎通確認
```bat
ping IPアドレス
```
##### 自身のリッスン状態の確認
```bat
netstat -ano
```
##### 通信先のポートが開ているかの確認
```bat
ftp
> open IPアドレス ポート番号
・・・
> quit
で終了
```
##### DNSの確認
```bat
nslookup ホスト名/IPアドレス
```
##### ネットワーク経路の確認
```bat
tracert ホスト名/IPアドレス
```
##### httpリクエスト
```bat
curl -X "GET" "UR" -v | jq.exe
```
[jq公式サイト](https://stedolan.github.io/jq/)

#### コマンドの結果をグレップする
```bat
コマンド | find "グレップする文字列"
```

#### 実行中のプロセス一覧
```bat
tasklist
```
