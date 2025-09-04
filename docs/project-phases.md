# Org-Mode Web Viewer 開発フェーズ

## プロジェクト概要

AWS Lightsail 上で org-mode ファイルを Web 表示するシステムを構築します。

### 主要機能
- Dropboxからのorg-modeファイル同期
- org-roamバックリンク表示
- グラフ可視化
- 個人専用アクセス（認証付き）

### アーキテクチャ
- **フロントエンド**: Unified/uniorgでorg-modeをパース
- **バックエンド**: Lightsail上の既存org-roam DBを活用
- **インフラ**: AWS Lightsailでホスティング

## 開発フェーズ

### Phase 1: 基本セットアップ
**目的**: プロジェクトの基盤を構築

- モノレポ構造の作成
  - packages/frontend
  - packages/backend
  - packages/shared
- 開発環境の構築
  - Docker Compose設定
  - 環境変数管理
  - 開発用スクリプト

### Phase 2: バックエンド API
**目的**: データ取得とAPIの基本実装

- org-roam DB との連携機能
- Dropbox からのファイル取得
- 認証システムの構築
- 必要なAPIエンドポイントの実装

### Phase 3: フロントエンド
**目的**: ユーザーインターフェースの実装

- **org-modeパース**
  - Unified/uniorg統合
  - ASTからHTMLへの変換
  - シンタックスハイライト

- **コアコンポーネント**
  - org-mode表示ビューア
  - バックリンクパネル
  - ファイルブラウザ

- **グラフ可視化**
  - D3.jsでのforce-directed graph
  - ノード間リンク表示
  - インタラクティブナビゲーション

- **UI/UX**
  - レスポンシブデザイン
  - キーボードショートカット

### Phase 4: デプロイ
**目的**: 本番環境への展開

- **AWS Lightsail設定**
  - コンテナサービス設定
  - ドメイン設定
  - HTTPS設定

- **CI/CDパイプライン**
  - GitHub Actions設定
  - 自動テスト
  - 自動デプロイ

- **監視・ログ**
  - エラー監視
  - パフォーマンス監視
  - ログ収集

## 技術スタック

### Frontend
- Next.js 14 (App Router)
- TypeScript
- Unified/uniorg (org-modeパース)
- D3.js (グラフ可視化)
- Chakra UI

### Backend
- FastAPI (Python) または Express (Node.js)
- SQLite (org-roam DB)
- Dropbox SDK
- JWT認証

### Infrastructure
- AWS Lightsail
- Docker
- GitHub Actions
- Nginx/Caddy

## 次のステップ

1. Phase 1の基本セットアップから開始
2. 各フェーズは順次実装し、必要に応じて調整
3. MVPを早期に作成し、イテレーティブに改善



