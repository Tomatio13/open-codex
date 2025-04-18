# Grokサポートの実装概要

Open Codex CLIにGrok AIモデルのサポートを追加しました。

## 実装内容

### 1. APIキーのサポート
- 環境変数 `GROK_API_KEY` を使用してGrok APIとの認証を行います
- APIキーが設定されていない場合のエラーメッセージを表示する機能を追加

### 2. エンドポイントの設定
- Grok APIのベースURL `https://api.grok.x/v1` を追加

### 3. デフォルトモデルの設定
- Grokのモデル `grok-1.5-preview` をデフォルトモデルとして追加
  - 両方のコンテキストモード（agentic および fullContext）で同じモデルを使用

## 使用方法

1. Grok APIキーを取得し、環境変数に設定します：
   ```sh
   export GROK_API_KEY="あなたのGrokAPIキー"
   ```

2. Codex CLIでGrokプロバイダーを使用するには、以下のいずれかの方法があります：
   
   a. コマンドラインオプションで指定：
   ```sh
   codex --provider grok "あなたのプロンプト"
   ```
   
   b. 設定ファイルで指定：
   ```sh
   codex config --provider grok
   ```

## 注意点

- Grok APIの仕様が変更された場合は、ベースURLやモデル名を適宜更新する必要があります
- Grok APIが提供する機能と互換性がない場合は、追加の対応が必要になる可能性があります 