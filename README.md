# Mautic ドキュメンテーション

### イントロダクション
本文書はオープソースのマーケティング自動化システムである[Mautic のドキュメンテーション](https://www.mautic.org/docs/index.html)を担うものです。コードはオープソースであり誰でも入手が可能です。この文書もまたオープンソースです｡本情報に改善が必要であると考える方々の支援をお待ちしています。｡

### PDF 版をダウンロード
[このリンクをクリックして](https://mautic.org/docs/mautic_docs.pdf) PDF 版をダウンロードしてください｡

### ドキュメンテーションの編集について
このレポジトリは [Gitbook](https://www.gitbook.com/) 向けのソースコードで [www.mautic.org/docs](https://www.mautic.org/docs/index.html) 上で公開されます。ソースコードは GitHub 上で共有されており，Mautic のコードをプログラマが編集するのと同じように誰でも編集が可能となっています。

#### 本文書の管理に Git を使う理由

- *バージョン*. 誰でも過去の版へアクセスができ，どのようなテキストだったか確認ができるため。
- *原著者*. 著者は各ファイルだけでなく一行一行に存在するため。.
- *コミュニティへのアシスト*. 同一文書内の誰かの文章を削除をしてしまう恐れが無いため。

クローン,変更，コミット，そして変更内容をプッシュするには Git に関するいくばくかの知識が必要です。GitHub のウェブインターフェイス上でファイルを直接変更しないようにする方法があります。すでに Git を使っている場合は好みのワークフローを使ってください｡まだ Git を使っていない場合は以下のガイドで Git を使って簡単に編集作業へ参加する方法を紹介します。

#### ブラウザ上でドキュメントを編集するEdit documents in a browser

1. あなたのアカウントにあるこのレポジトリには編集権限がまだありませんので最初に[フォーク](https://github.com/mautic/documentation#fork-destination-box) してください。
2. 編集するフィアルを選択します。そうするとファイル構造が下の方に表示されます｡ファイルの中身がどのようになっているかを確認するためにまず *README.md* ファイルをクリックして編集してみましょう。
3. *README.md* の中身と鉛筆アイコンの *Edit* ボタンが上の方に表示されます。それもクリックしましょう。
4. コンテンツは [Markdown markup](https://daringfireball.net/projects/markdown/) で書かれています｡. とても簡単なテキストベースのフォーマットです｡
5. ファイルに変更を加えてください｡たとえば末尾に`これが最初の貢献`と加えるのもいいでしょう｡
6. When you made a change, scroll down and notice the form called *Commit changes*. This is important. To save a change, you have to describe what you've changed and why. Write for example `A new line added for testing purposes`. Do not save yet!
7. Because the GitHub web interface does not provide all features of git, we won't have an easy way to revert our change back to the original state. We'd have to create another commit where we'd delete the added line. That would make a mess in the commit history. So instead, we create a new branch. There is a checkbox for it "Create a new branch...". The branch has to have a name. `{yourusername}-patch-1` will be prefilled. Let's change it to `{yourusername}-testing`. Click the *Propose file change* now.
8. Ok, so the change exists in your repository now. To propose the change to the official repository, you have to send a pull request (PR). You've been redirected to do just that. Here you describe your proposed change and click (please don't send the testing PRs) the *Create pull request* button.

If you want to clean after the testing, go to the *Branches* section and delete the testing branch.

#### The file structure

We've worked with the *README.md* file in the previous section. This file is shown in the home page of a GitHub repository and you are reading its content right now. It doesn't have anything to do with the Mautic documentation.

The *SUMMARY.md* file defines the menu of the documentation. If you'll add a new page to the documentation, you'll have to also add a new line there defining the title and the link to the file. It's pretty straightforward when you'll see the current menu items.

The folders are here to group the topics together. Open for example the *asset* folder. You'll see it has its own *README.md* file. It is the main content when you click on the Asset menu item. The *manage_assets.md* file is a subitem. The *media* subfolder contains all the images used in the *md* files.

#### Links

Often you'll want to make a link into another place of the documentation. In Markdown, the link looks like this:

```
[link title](http://example.com)
```

This will create an external link with absolute URL. If you want to create an internal link, use the relative URL like this:

```
[these steps](./../plugins/integration_test.html)
```
This will link to `plugins/integration_test.html` on the documentation website created from the *md* source file.

#### Images

As noted above, the images can be placed in the media subfolders. The images probalby isn't possible to upload via the GitHub web interface, but you can upload them to any public URL and link them from there.

```
![alternative text here](http://example.com/images/apple.png "Tooltip text here")
```
Or, if you'd want to display an image already uploaded to the documentation repository, you can use relative path:

```
![alternative text here](/assets/media/assets-newcategory.png "Tooltip text here")
```
