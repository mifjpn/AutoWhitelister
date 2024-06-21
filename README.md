# AutoWhitelister
## 使い方
### 動作
　Whitelist制の、Spigot～Purpur系の標準出力（エラー出力を含む）を1行ずつ解釈し、MCID UUIDを取得します。その後、banにMCID,UUIDがない事とWhitelistに未登録の場合、Whitelistにそれらをつけ足します。そしてRconポートに"witelist reload"を送り、Whitelistの書き換えを有効にします。クライアントが最初のアクセスだった場合、「接続できません・・・（以下設定された文言）」が出て1回目のアクセスはキックされます。
### 準備
　ファイル群は~/binに置くことをお勧めします。そして、各シェルスクリプト等は実行属性を与えてください。また、スクリプトには、スクリプトがおかれている絶対パスやサーバの置かれている絶体パスや各種ファイル名、RCONポートのパスワード（server.propertiesと同じ）が記載されて得いますので、自分の環境に合わせて設定してください。


## How to use
### Script behavior

The script obtains the MCID UUID by interpreting the standard output (including error output) of the Whitelist system Spigot and Purpur line by line.
After that, if the obtained MCID or UUID is not registered in the Banlist or Whitelist, the script adds them to the Whitelist and sends "whitelist reload" to the Rcon port.
The script thus enables whitelist rewriting.
If the client is accessing for the first time, "Unable to connect... (sentence set by spigot.yml)" will appear and the first access will be kicked.

### Preparation
We recommend placing the file in ~/bin.Next, give execution attributes to each shell script etc.The script also contains the absolute path where the script is located, the absolute path where the server is located, various file names, and the RCON port password (same as server.properties).Please set it according to your environment.

### サーバのログを1行づつ処理させるためのパイプの実行の仕方
例

>$ java -server -Xmx12G -Xms10G -XX:+UnlockExperimentalVMOptions -XX:+UseG1GC -XX:MaxGCPauseMillis=50 -XX:G1NewSizePercent=20 -XX:G1MaxNewSizePercent=60 -XX:MetaspaceSize=512M -XX:MaxMetaspaceSize=512M -XX:+UseCompressedOops -XX:CompressedClassSpaceSize=512M -XX:G1HeapRegionSize=32M -XX:ParallelGCThreads=4 -XX:+UnlockExperimentalVMOptions -XX:+UseJVMCICompiler --add-modules=jdk.incubator.vector -jar purpur-1.20.6-2233.jar |& xargs -n1 -d'\n' /home/[YourUserDIR]/bin/whitelister

の様に

>|& args -n1 -d'\n'

を使います。

### How to run a pipe to process server logs line by line
Example

>$ java -server -Xmx12G -Xms10G -XX:+UnlockExperimentalVMOptions -XX:+UseG1GC -XX:MaxGCPauseMillis=50 -XX:G1NewSizePercent=20 -XX:G1MaxNewSizePercent=60 -XX:MetaspaceSize=512M -XX:MaxMetaspaceSize=512M -XX:+UseCompressedOops -XX:CompressedClassSpaceSize=512M -XX:G1HeapRegionSize=32M -XX:ParallelGCThreads=4 -XX:+UnlockExperimentalVMOptions -XX:+UseJVMCICompiler --add-modules=jdk.incubator.vector -jar purpur-1.20.6-2233.jar |& xargs -n1 -d'\n' /home/[YourUserDIR]/bin/whitelister

like

>|& args -n1 -d'\n'

use.

### Whitelistエラーの場合のメッセージについて
　クライアントには初期ログインではサーバからエラーメッセージが出ます。そこで「あなたの情報を審査設定中である」ことと、「問題がない間合いは再度ログインしてほしい」旨表示します。例えば以下のようなメッセージをサーバに設定します。

>Example
>
>in spigot.yml
>
>messages:
>  whitelist: あなたの情報を審査中です。審査を通ればログインリストに登録されます。少し待った後（10秒程度）もう一度ログインしてみてください。ログインできない場合はDiscordなどで管理>者にご連絡ください。（https:///・・・を見てください）`

### サーバ側のRconのパスワードもスクリプトと同様に決めて設定してください

>in server.propaties
>
>rcon.password=somting-pass-word
>rcon.port=25575

### About the message when whitelist error occurs

The client receives an error message from the server upon first login.Therefore, the message "We are reviewing your information" and "If there is no problem, please log in again" will be displayed to the client.For example, set the following message on the server.

>Example
>
>In spigot.yml
>
>Message:
> Whitelist: Your information is currently under review. If your application passes the screening, it will be added to the login list. Please wait for a while (about 10 seconds) and then log in again. If you are unable to log in, please contact the administrator via Discord etc. (see https:///...)`

### Decide and set the server-side Rcon password in the same way as the script.

>in server.properties
>
>rcon.password=Somting Password
>rcon.port=25575

## 総括
悪意のある行動をするものは自分の記録をとられることを嫌います。少なくともWhitelistにUUIDを記録された時には、banしやすいことになります。そのため悪意のあるもののログインを抑制できます。

## Summary
Those who act maliciously do not like to have their records taken. At least when the UUID is recorded in the whitelist, it will be easier to ban. Therefore, malicious logins can be suppressed.
