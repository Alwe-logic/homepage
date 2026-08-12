# GitHub Pages での公開

このプロジェクトは GitHub Pages へデプロイできるよう設定済みです。`main` ブランチへ push すると、GitHub Actions が自動で静的サイトをビルドして公開します。

## 最初の一回だけ行うこと

1. GitHub で新しいリポジトリを作成します。通常のプロジェクト名（例: `researcher-homepage`）で構いません。
2. このフォルダで以下を実行します。

   ```bash
   git add .
   git commit -m "Initial website"
   git branch -M main
   git remote add origin https://github.com/ユーザー名/リポジトリ名.git
   git push -u origin main
   ```

3. GitHub のリポジトリ画面で **Settings → Pages** を開き、**Build and deployment** の **Source** を **GitHub Actions** にします。

数分後、`https://ユーザー名.github.io/リポジトリ名/` でサイトが公開されます。将来、`username.github.io` という名前のリポジトリを作る場合は、トップレベルの URL で公開できます。

## Notes の扱い

Notes は公開サイト上では非表示にしていますが、現在の原稿はこのプロジェクト内に保存されています。リポジトリを **Public** にすると、サイトからは見えなくても原稿ファイル自体は GitHub 上で閲覧できます。

原稿も非公開にしたい場合は、まずリポジトリを **Private** にして公開できるか確認してください。Private リポジトリからの GitHub Pages が利用できないアカウントの場合は、原稿を含む非公開の作業用リポジトリと、公開用のリポジトリを分ける構成にします。
