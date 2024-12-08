# MetagriLabo Thanks Gift (MLTG) Web Application

このプロジェクトは、NFTを活用したデジタル商品交換システムを実装したWebアプリケーションです。MetaMaskウォレットと連携し、ユーザーが所有するNFTを実物商品と交換できる機能を提供します。

## 機能概要

このアプリケーションは以下の主要機能を提供します：

- MetaMaskウォレットとの連携による認証
- NFTコレクションの表示と管理
- NFTを使用した商品交換システム
- マルチチェーンサポート（Ethereum、Goerli、Polygon、Mumbai）

## プロジェクト構造

```
MLTGwebApp/
├── .env                 # 環境変数設定ファイル
├── .firebase/          # Firebaseデプロイメント設定
├── .firebaserc         # Firebase設定ファイル
├── firebase.json       # Firebaseプロジェクト設定
├── package.json        # プロジェクト依存関係と設定
├── public/            # 静的ファイルディレクトリ
└── src/               # ソースコードディレクトリ
    ├── App.js         # メインアプリケーションコンポーネント
    ├── App.css        # アプリケーションスタイル
    ├── index.js       # アプリケーションエントリーポイント
    └── images/        # 画像ファイルディレクトリ
```

## 主要ファイルの説明

### App.js
メインのアプリケーションロジックを含むファイルです。以下の機能を実装しています：
- MetaMaskとの接続管理
- NFTコレクションの取得と表示
- 商品交換フォームの処理
- Web3トランザクションの実行
- AirTableとの連携

### package.json
プロジェクトの依存関係を管理します。主要な依存パッケージ：
- @thirdweb-dev/react: NFT機能の実装
- @thirdweb-dev/sdk: Web3開発用SDK
- ethers: Ethereum開発ライブラリ
- react-bootstrap: UIコンポーネント
- react-router-dom: ルーティング

### .env
環境変数を管理するファイルです。現在の設定：
- GENERATE_SOURCEMAP: ソースマップ生成の制御

### firebase.json
Firebaseのホスティング設定を管理します。

## 技術スタック

- フロントエンド: React.js
- UI Framework: React Bootstrap
- Web3連携: ThirdWeb SDK, ethers.js
- ウォレット連携: MetaMask
- データベース: AirTable
- ホスティング: Firebase
- 画像ストレージ: IPFS

## セットアップと開発

開発環境のセットアップ:

```bash
# 依存関係のインストール
npm install

# 開発サーバーの起動
npm start

# プロダクションビルド
npm run build

# Firebaseへのデプロイ
firebase deploy
```

## 必要な環境変数

本番環境では以下の環境変数の設定が必要です：

- AIRTABLE_API_KEY: AirTableへのアクセスキー
- WEB3_API_KEY: ThirdWebのAPIキー
- MORALIS_API_KEY: MoralisのAPIキー

## NFT商品交換の流れ

1. ユーザーがMetaMaskでウォレットを接続
2. 所有するNFTの一覧が表示される
3. 交換したいNFTを選択
4. 配送情報フォームに必要事項を入力
5. MetaMaskで取引を承認
6. NFTが管理者ウォレットに転送され、商品発送手続きが開始

## セキュリティ考慮事項

- MetaMask認証による安全なトランザクション
- 環境変数による機密情報の保護
- Web3 APIキーによるアクセス制御
- AirTableとの安全な連携

## 注意事項

- 本システムはテストネットでの利用を推奨します
- 実際の商品交換には管理者の承認が必要です
- NFTの転送には適切なガス代が必要です

## 貢献

プロジェクトへの貢献を歓迎します。プルリクエストを送る前に以下をご確認ください：
- コードスタイルガイドラインの遵守
- テストの実施
- ドキュメントの更新

## ライセンス

This project is licensed under the MIT License - see the LICENSE file for details

## 開発者向け情報

- API仕様書は`/docs`フォルダを参照してください
- 開発環境の構築手順は`CONTRIBUTING.md`を参照してください
