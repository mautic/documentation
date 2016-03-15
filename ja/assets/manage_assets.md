# アセットの管理
## カテゴリ
アセットは，あなたが簡単にリソースを検索することを可能にし，カテゴリとして整理することができます。新しいカテゴリを作成するには、アセットのセクションを参照し，[カテゴリの管理] をクリックします。

### カテゴリの作成
新しいカテゴリを作成するには画面右上にある [新規作成] をクリックしてください

![新規アセットカテゴリーの作成](/assets/media/assets-newcategory.png "Create a new category")

使用される「ファイリングシステム」の構造を反映するようなカテゴリの名前を付け，カテゴリの短い説明を付け加えてください。

エイリアスフィールドは手動で指定しない限り，自動的にタイトルフィールドから移入されます。これは理想的な URL パスを作成するために使用され，スペースの代わりにハイフンが含まれている必要があります。

これは、16進法のカラーコードの入力やカラーピッカーで色を選択して個々のカテゴリを色分けすることができます。

カテゴリを公開してアセットを割り当て，利用できるようにするには [はい] が強調表示されている用にしてください。カテゴリを公開しないよう設定するには [いいえ] をクリックしてください。

変更内容を保存し，編集を続行するには [適用] ボタンを押してください。変更を保存しカテゴリ画面へ戻るには [保存して閉じる] をクリックしてください。操作をキャンセルしてカテゴリ画面へ戻るには [キャンセル] を押してください。

### カテゴリの編集
カテゴリを編集するには，カテゴリ名をクリックするか横にあるチェックボックスにチェックを入れ [編集] をクリックしてください。上のスクリーンショットと同じな画面が表示されてきます。各入力フィールドがすでに埋められている点が違うくらいです。これも上と同じように編集して保存ができます。

### カテゴリの管理
カテゴリはカテゴリ名または ID でソートできます。カラムのヘッダを必要なフィールドで検索するにはカラムヘッダをクリックしてください。再度クリックすることでソート順を逆にできます。

![Sorting categories](/assets/media/assets-managecategories.png "Sorting categories")

ページの下部にあるドロップダウンでページごとに表示されるカテゴリの数を制御することができます。この番号はカテゴリの数が一定数を超えている場合，ページネーションの矢印でページ間を移動できます。表示されるカテゴリの数を変更するには，ドロップダウンリストから希望の番号を選択する事でページが自動的に更新されます。

### カテゴリの削除

矢印横にあるチェックボックスにチェックを入れて削除を選択する事で，カテゴリを削除できます。アセットの割り当てられているカテゴリが削除されても，アセットは削除されず，'未アサイン' と表示されます。実際にカテゴリを削除する際には警告が表示されます。

![Delete an asset category](/assets/media/assets-deletecategory.png "Delete a new category")

## アセット

アセットは多くの場合，フォームを完了してもらうためやのインセンティブとして提供され，これにはホワイトペーパー，インフォグラフィック，動画，mp3 等を含める事ができます。アセットはMautic内でダウンロード可能なファイルとして利用可能な状態におかれ，フォームの送信後に簡単にダウンロードできたり，またはあとでアクセス可能なリンクとして提供されます。

アセットを作成するには，まず必要とされる任意のカテゴリを作成し，公開されていることを確認してください。未公開のカテゴリにアセットを割り当てることはできません。

アセットの作成を開始するには 'アセットの管理' へ移動し，[新規作成]をクリックします。

![Create a new asset](/assets/media/assets-newasset.png "Create a new asset")

アセットはコンピュータのローカルリソースやリモートから追加できます。ローカルからアップロードする場合，
Assets can be added from local resources on a computer or from a remote location.  Local uploads will be restricted by size due to the settings of your server - any such restriction may be advised as a warning above the file upload area.

### Uploading an asset

To upload an asset, either drag the file into the white box, or click in the white box to open a file upload window.  On selection of the file, it will be automatically uploaded and will appear in the white box.  

![Assigning an asset to a category](/assets/media/assets-uploadnewassetunpublishedcategory.png "Assigning an asset to a category")

The title of the asset can be set, along with a description and an alias as above with categories.  Assets can only be assigned to published categories, therefore the dropdown list for category selection will not feature unpublished categories.  It is also possible to set the language, whether the asset is published or unpublished, and whether it should become published or unpublished at a specific date or time.

When the details have been completed, click 'Save & Close' or 'Apply' to save changes to the asset.

### Viewing an asset

Once an asset has been uploaded and saved, it can be viewed by clicking on the asset name in the list of assets.

![Viewing an asset](/assets/media/assets-viewasset.png "Viewing an asset")

The view asset screen gives information about the number of times the asset has been downloaded, which can be displayed on a chart by hourly, daily, weekly, monthly or yearly downloads.  The graph also shows the number of unique, versus total views - this is an indication of whether the same asset is being downloaded multiple times by some visitors.

A download URL allows previewing of the asset - clicking on the link will open the asset in a new window.

Below the preview link will be displayed recent activity for this resource, with a preview of the resource being available beneath the chart for some formats.

### Editing an asset

An asset can be edited by clicking on the 'edit' button while viewing the asset, or by selecting the arrow next to the checkbox for the asset, and selecting 'edit'.  The edit screens are the same as the view screens, however content will be populated in the fields.

### Deleting an asset

An asset can be deleted by clicking on the 'delete' button while viewing the asset, or by selecting the arrow next to the checkbox for the asset, and selecting 'delete'.  A confirmation screen will be displayed, prompting confirmation that the asset should be deleted.

Once an asset has been deleted, it cannot be retrieved, and statistics relating to the number of downloads for that asset will no longer be available.  Lead points that may have been accumulated as a result of accessing the resource will remain. It is recommended where possible to unpublish assets which are no longer in use - in future there may be an archive feature.


