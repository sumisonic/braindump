# CLAUDE.md - Braindump Project

## プロジェクト概要

このプロジェクトは、AWS Lightsail 上で org-mode ファイルを Web 表示するシステムです。
org-roam のバックリンク機能とグラフ可視化を提供します。

## プロジェクト構造

```
braindump/
├── packages/
│   ├── frontend/      # Next.js フロントエンド
│   ├── backend/       # API サーバー
│   └── shared/        # 共通型定義
├── docs/             # ドキュメント
├── docker/           # Docker 設定
└── scripts/          # ユーティリティスクリプト
```

## 技術的な重要事項

### Frontend
- **org-modeパース**: Unified/uniorgを使用してクライアントサイドでパース
- **グラフ可視化**: D3.jsでforce-directed graphを実装
- **状態管理**: Zustand または React Context
- **スタイリング**: Chakra UI

### Backend
- **既存リソース**: Lightsail上に既存のorg-roam DBがある
- **Dropbox連携**: Dropbox APIでorg-modeファイルを同期
- **認証**: JWT実装で個人専用アクセス制御

### Infrastructure
- **ホスティング**: AWS Lightsail
- **データベース**: 既存のorg-roam DB (SQLite)
- **ファイルストレージ**: Dropbox

## 開発ガイドライン

### コーディング規約
- TypeScriptを使用
- ESLint/Prettierの設定に従う
- コンポーネントは関数コンポーネントで実装
- カスタムフックでロジックを分離

### Git 戦略
- mainブランチは常にデプロイ可能な状態を保つ
- 機能開発はfeatureブランチで行う
- コミットメッセージは日本語でも英語でも可

### テスト
- 重要なビジネスロジックには単体テストを書く
- E2Eテストは主要なユーザーフローをカバー

## 現在のフェーズ

Phase 1: 基本セットアップ（開始前）

詳細は `docs/project-phases.md` を参照してください。

## 環境変数

```env
# Backend
DROPBOX_ACCESS_TOKEN=
JWT_SECRET=
DATABASE_URL=

# Frontend
NEXT_PUBLIC_API_URL=
```

## よく使うコマンド

```bash
# 開発環境起動
pnpm dev

# ビルド
pnpm build

# テスト実行
pnpm test

# リント実行
pnpm lint
```

## 注意事項

1. org-roam DBは既にLightsail上に存在するため、新規作成は不要
2. 認証は個人専用のため、シンプルな実装で良い
3. パフォーマンスよりも機能の完成を優先
4. モノレポ構成でパッケージ間の依存関係を明確にする

## 参考リンク

- [Unified](https://unifiedjs.com/)
- [uniorg](https://github.com/rasendubi/uniorg)
- [org-roam](https://www.orgroam.com/)
- [AWS Lightsail](https://aws.amazon.com/lightsail/)


