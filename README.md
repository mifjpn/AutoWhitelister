# AutoWhitelister
- 使い方
　Whitelist制の、Spigot～Purpur系の標準出力（エラー出力を含む）を1行ずつ解釈し、MCID UUIDを取得します。
　その後、banにMCID,UUIDがない事とWhitelistに登録されていない場合、Whitelistにつけ足して、Rconポートに

Parses the purpur server's standard output (log) line by line. The client will receive a warning the first time it receives a kick from the server via the whitelist. Then register them in Whitelist.json after checking them.
