# X Posts Collection

X (Twitter) の投稿データを収集・保存するリポジトリ

## 構造

```
x_posts/
├── bookmarks/
│   ├── main_account/           # メインアカウント (@numa_vibehacker)
│   │   ├── index.json          # ブックマーク一覧（メタデータ付き）
│   │   ├── changelog.json      # 変更履歴
│   │   └── posts/              # 個別投稿の詳細データ
│   │       └── {status_id}.json
│   └── sub_account/            # サブアカウント（将来用）
└── posts/                      # 投稿データ（将来用）
```

## データ形式

### index.json（ブックマーク一覧）

```json
{
  "account": "numa_vibehacker",
  "last_updated": "2026-01-23T19:26:54",
  "total_count": 220,
  "bookmarks": [
    {
      "status_id": "投稿ID",
      "username": "投稿者のユーザー名",
      "first_seen": "初めて検出した日付 (YYYY-MM-DD)",
      "has_detail": false
    }
  ]
}
```

| フィールド | 説明 |
|-----------|------|
| `status_id` | 投稿の一意ID |
| `username` | 投稿者のユーザー名 |
| `first_seen` | このブックマークを初めて検出した日付 |
| `has_detail` | 詳細データを取得済みかどうか |

### changelog.json（変更履歴）

```json
{
  "entries": [
    {
      "date": "2026-01-23",
      "total_after": 220,
      "added_count": 220,
      "removed_count": 0,
      "note": "Initial collection"
    }
  ]
}
```

差分管理用。新規追加・削除されたブックマークを追跡。

### posts/{status_id}.json（個別投稿詳細）

```json
{
  "status_id": "投稿ID",
  "username": "ユーザー名",
  "display_name": "表示名",
  "text": "投稿本文",
  "created_at": "投稿日時",
  "fetched_at": "取得日時",
  "metrics": {
    "likes": 0,
    "retweets": 0,
    "replies": 0
  },
  "media": []
}
```

## バージョン管理の仕組み

- **新規ブックマーク検出**: `first_seen` に検出日を記録、`has_detail: false`
- **詳細取得後**: `has_detail: true` に更新
- **削除検出**: `changelog.json` の `removed_count` で追跡
- **差分確認**: 前回との比較で追加・削除を特定

## 収集履歴

| 日付 | アカウント | 件数 | 備考 |
|------|-----------|------|------|
| 2026-01-23 | @numa_vibehacker | 220 | 初回収集 |
