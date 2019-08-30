---
layout: default
title: パッケージを登録する
nav_order: 2
parent: Japanese
permalink: /ja/publish
---

# パッケージを登録する

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 事前準備

### 未登録の場合

コマンドラインからユーザ登録を行います。

```bash
npm adduser --registry https://upm-packages.dev
```

認証情報が `~/.npmrc` に記録されます。

### 登録済みの場合

既に登録済みの場合は、コマンドラインからログインを行います。

```bash
npm login --registry https://upm-packages.dev
```

認証情報が `~/.npmrc` に記録されます。

## パッケージ登録

### 1. 通常の Unity プロジェクトとしてパッケージを開発する

原則的に Unity 2019.1.0f2 以降のバージョンでの開発を推奨しています。

開発するパッケージが Unofficial Unity Package Manager Registry で管理されている他のパッケージに依存していても問題ありません。

### 2. `.npmrc` を配置する

以下の内容を記した `.npmrc` をプロジェクトのルートディレクトリに配置します。

```rc
registry=https://upm-packages.dev
```

### 3. `package.json` を配置する

次に例示するような `package.json` を **`Assets/` 直下** に配置します。

```json
{
    "name": "dev.monry.upm.sample-package",
    "displayName": "Sample Package",
    "version": "1.0.0",
    "unity": "2019.1",
    "description": "Sample Package for Unofficial Unity Package Manager Registry",
    "author": {
        "name": "Tetsuya Mori",
        "url": "https://github.com/monry"
    },
    "license": {
        "type": "MIT",
        "url": "https://monry.mit-license.org"
    },
    "keywords": ["sample"],
    "category": "",
    "dependencies": {
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/monry/Sample-Package"
    }
}
```

次のフィールドは必須項目です。

* name
* displayName
* version

原則的に [package.json がサポートするフィールド](https://docs.npmjs.com/files/package.json) が利用可能です。

Unity Package Manager でインストールされた際のエラーを回避するために `package.json.meta` も生成されるように `package.json` を Unity Editor 上でインポートしておきましょう。

### 4. publish する

`npm` コマンドや `yarn` コマンドを用いてパッケージを Unofficial Unity Package Manager Registry に publish します。

```bash
npm publish Assets
```

```bash
yarn publish Assets
```

なお、パッケージの更新を行う際には、 `package.json` の `"version"` フィールドの値が変更されている必要があります。
