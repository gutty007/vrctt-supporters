# vrctt-supporters

VRChatワールド **VRC卓球 (VRCTableTennis)** の支援者名簿を配信するための公開リポジトリです。

## 配信URL

```
https://gutty007.github.io/vrctt-supporters/v1/supporters.txt
```

ワールド側は `VRCStringDownloader` でこのURLを取得し、ローカルプレイヤーの表示名と照合して特典を解放します。

## フォーマット (v1)

TSV（タブ区切り）。1行1人。

```
displayName<TAB>level<TAB>skinId
```

| 列 | 内容 |
|---|---|
| displayName | VRChatの表示名（Discordの /vrc登録 で本人が入力したもの） |
| level | `1` = サポーター / `2` = スポンサー（数値なので「N以上」で判定可能） |
| skinId | 解放するスキンのID。指定なしは `-` |

- `#` で始まる行はコメント（ヘッダ情報）。
- 空行は無視。
- 改行コードは LF。文字コードは UTF-8。
- パスに `/v1/` を含めることで、将来フォーマットを変更しても旧バージョンのワールドが壊れないようにしています。

## 更新方法

非公開リポジトリの GitHub Actions が1時間ごとに以下を突き合わせて `v1/supporters.txt` を生成し、このリポジトリへ push します。

1. Patreon API（自動）
2. Cloudflare KV（Discordの `/vrc登録` で登録されたDiscord ID → VRChat表示名の対応）
3. 手動リスト（Patreon以外の支払い者）

※ 現在は自動化未実装のため、上記はサンプルデータです。

## プライバシーについて

このファイルに含まれるのは **本人がDiscordの `/vrc登録` で自分で入力したVRChat表示名のみ** です。
DiscordのユーザーIDやユーザー名、Patreonのアカウント情報、メールアドレス等は一切含まれません。

登録フォームには「入力した表示名は公開名簿に掲載されます」と明記してください。
