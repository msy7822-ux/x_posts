# X Posts Collection

X (Twitter) の投稿データを収集・保存するリポジトリ

## 構造

```
x_posts/
├── bookmarks/
│   ├── main_account/    # メインアカウント (@numa_vibehacker) のブックマーク
│   └── sub_account/     # サブアカウントのブックマーク
└── posts/               # 投稿データ（将来用）
```

## データ形式

### ブックマーク (bookmarks/*.json)

```json
{
  "account": "アカウント名",
  "collected_at": "収集日時 (ISO 8601)",
  "total_count": 件数,
  "bookmarks": [
    {
      "username": "投稿者のユーザー名",
      "status_id": "投稿ID",
      "url": "投稿URL"
    }
  ]
}
```

## 収集履歴

| 日付 | アカウント | 件数 |
|------|-----------|------|
| 2026-01-23 | @numa_vibehacker | 220 |
