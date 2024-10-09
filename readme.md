# sample-ts-lib-github-packages

このリポジトリは、プライベートNPMパッケージとしてGitHub Packagesに公開されたTypeScriptライブラリです。このライブラリは、2つの数字型引数を受け取り、その合計を返す関数を提供します。

## 目次
- [ライブラリの作成](#ライブラリの作成)
- [GitHub Packagesへの公開](#github-packagesへの公開)
- [サンプルアプリの作成](#サンプルアプリの作成)
- [注意事項](#注意事項)

## ライブラリの作成

1. リポジトリの作成
   - GitHubで新しいリポジトリを作成します。リポジトリ名は `sample-ts-lib-github-packages` にします。

2. ローカル環境のセットアップ
```bash
   mkdir sample-ts-lib-github-packages
   cd sample-ts-lib-github-packages
   pnpm init
```

3. TypeScriptと必要な依存関係のインストール
```
pnpm add -D typescript @types/node ts-node

```
4. TypeScript設定ファイルの作成
```
npx tsc --init

```

5. ライブラリの実装
```
export function add(a: number, b: number): number {
    return a + b;
}

```
6. パッケージ情報の更新
```
{
    "name": "@<your-github-username>/sample-ts-lib-github-packages",
    "version": "1.0.0",
    "main": "dist/index.js",
    "types": "dist/index.d.ts",
    "scripts": {
        "build": "tsc"
    },
    "publishConfig": {
        "registry": "https://npm.pkg.github.com/"
    },
    "repository": {
        "type": "git",
        "url": "git+https://github.com/<your-github-username>/sample-ts-lib-github-packages.git"
    },
    "author": "",
    "license": "ISC"
}

```

## step2. GitHub Packagesへの公開
### 1. Gitの初期化とコミット
```
git init
git add .
git commit -m "Initial commit"

```

### 2. リモートリポジトリへのプッシュ
```
git remote add origin https://github.com/<your-github-username>/sample-ts-lib-github-packages.git
git push -u origin master

```

### 3. パッケージのビルド
```
pnpm run build

```

### 4. Githubにパッケージを公開
アクセストークンを作成する
[トークンの作成](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

.npmrcにトークンを記載する(非推奨)

```
npm publish --access=restricted

```