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
   - 通常の商品：基本配送情報のみ
   - Tシャツ：サイズ選択を含む追加情報
5. MetaMaskで取引を承認
6. NFTが管理者ウォレットに転送され、商品発送手続きが開始

## オリジナルTシャツ交換システム

NFTコレクションの中でも、特定のTシャツ交換用NFTについては、以下の特別な仕様が実装されています：

### サイズ選択システム

商品交換時に、以下のサイズオプションから選択できます：
- 標準サイズ：S、M、L、XL
- カスタムサイズ：「その他」オプションで自由入力可能

### 対象NFT
以下のKey IDを持つNFTがTシャツ交換の対象となります：
- rec65kFu48ut5GPhC
- recB1VbiT6bR7TMnH
- recqCurt5f435BcVf
- recj2JF2UnJU2ixXw
- reclz4Dg5QS8VnJZ0
- recyBnzU9IzYtJuCT
- recK0sK8Hzq6ffghW
- recs6Mdq8UFgEjpPD
- recjmIXtdNbAdMQnd
- rec5noihUnn4JYDeV
- recCafjYmJ2gX9K0l
- reclxuPXKWLkCjmVE

### データ管理
選択されたサイズ情報は以下の形式でAirTableに保存されます：
- Size: 標準サイズ（S/M/L/XL）の選択値
- Size_Other: カスタムサイズの入力値

### 使用方法
1. 対象のTシャツNFTを選択
2. フォームにて配送情報を入力
3. 希望のサイズを選択（標準サイズまたはカスタム）
4. 入力内容を確認して申し込みを実行

## MetaMaskウォレット連携仕様

このアプリケーションではMetaMaskとの連携を通じて、安全なブロックチェーン取引を実現しています。

### ウォレット接続システム

MetaMaskとの接続は以下の3つのコア機能で構成されています：

1. アカウント接続機能
   - eth_requestAccountsメソッドを使用したウォレット接続
   - ユーザーの承認フローの管理
   - 接続状態の監視と維持

2. ネットワーク管理機能
   - 対応チェーンの自動識別（Ethereum、Goerli、Polygon、Mumbai）
   - チェーンIDの取得と検証
   - ネットワーク切り替えの検知と処理

3. トランザクション管理機能
   - NFT転送時のトランザクション作成
   - ユーザー署名の要求と検証
   - トランザクション状態の監視

### 対応ネットワーク

システムは以下のブロックチェーンネットワークに対応しています：

- Ethereum Mainnet (Chain ID: 1)
- Goerli Testnet (Chain ID: 5)
- Polygon Mainnet (Chain ID: 137)
- Mumbai Testnet (Chain ID: 80001)

### セキュリティ仕様

1. トランザクション保護
   - すべてのNFT転送操作に署名要求
   - トランザクション内容の詳細表示
   - 不正なネットワークからの保護

2. エラー処理
   - ユーザーによる操作拒否の適切な処理
   - ネットワークエラーのハンドリング
   - 接続タイムアウトの管理

3. 状態管理
   - ウォレット接続状態の永続的監視
   - アカウント切り替えの自動検知
   - ネットワーク変更の追跡
     
### イベント管理システム

システムは以下のイベントを常時監視し、適切に対応します：

- accountsChanged: アカウントの切り替え検知
- chainChanged: ネットワークの切り替え検知
- connect: 接続確立の検知
- disconnect: 接続切断の検知

### 使用APIメソッド

MetaMaskとの通信には以下のAPIメソッドを使用しています：

- eth_requestAccounts: ウォレット接続の要求
- eth_chainId: チェーンIDの取得
- eth_sendTransaction: トランザクションの送信
- personal_sign: メッセージ署名の要求    

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
