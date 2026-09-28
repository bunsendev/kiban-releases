# kiban-releases

ブンセン予測基盤 Field Pilot の**署名済み更新ファイル配布専用**リポジトリです。開発・ビルドは [bunsendev/kiban](https://github.com/bunsendev/kiban) で行います。現場PCの更新確認先は、このリポジトリの公開GitHub Releasesです。

## 公開Releaseの契約

各Releaseのタグは `v0.1.0-field-pilot.N`（pilot）または `vMAJOR.MINOR.PATCH`（stable）とし、次の4ファイルを添付します。

- `BunsenFieldPilot-<version>.zip`: ソースを含まないWindows配布パッケージ
- `manifest.json`: 版・channel・最低版・パッケージ名・サイズ・SHA-256等
- `manifest.sig`: manifest.jsonのEd25519署名
- `SHA256SUMS.txt`: パッケージのSHA-256

公開前に開発リポジトリ側のテスト、配布物の内容監査、`release_preflight.py` を通してください。実データ、現場固有設定、Token、APIキー、秘密鍵、Python/PowerShellソースをこのリポジトリやReleaseに置かないでください。現行のソース同梱Field Pilot ZIP/RC4インストーラーは公開不可です。

## 信頼の起点

現場インストーラーにEd25519公開鍵を同梱し、`Data/Config/release-update-public.pem` に固定します。秘密鍵は配布しません。アプリはこのリポジトリのReleaseを匿名で確認し、署名とパッケージのサイズ・SHA-256を検証します。GitHub上のファイルだけで鍵の初回信頼を確立することはできません。鍵の生成・運用手順は開発リポジトリの `planning/GITHUB_RELEASE_AUTO_UPDATE_RESULT.md` を参照してください。

配布用のバイナリ、更新適用・移行・ロールバックの受入が完了するまではReleaseを発行しません。
