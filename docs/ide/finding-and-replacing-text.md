---
title: テキストの検索と置換
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106753"
---
# <a name="find-and-replace-text"></a>テキストの検索と置換

[[検索と置換]](#find-and-replace-control) または [[フォルダーを指定して検索]/[フォルダーを指定して置換]](#find-in-files-and-replace-in-files) を使用して、Visual Studio エディターでテストを検索したり、置換したりすることができます。

> [!TIP]
> 変数やメソッドなど、コード記号の名前を変更している場合、検索と置換よりも*[リファクター](../ide/reference/rename.md)* を使用する方が適しています。 検索と置換でやみくもにすべてのインスタンスを置換しても、リファクタリングはインテリジェントで、範囲を理解します。

検索と置換機能は、エディター、その他の特定のテキストベースのウィンドウ (**[検索結果]** ウィンドウなど)、デザイナー ウィンドウ (XAML デザイナー、Windows フォーム デザイナーなど)、およびツール ウィンドウで利用できます。

検索のスコープは、現在のドキュメント、現在のソリューション、またはカスタム フォルダー セットに設定できます。 複数ファイル検索用に、一連のファイル名拡張子を指定することもできます。 .NET [正規表現](../ide/using-regular-expressions-in-visual-studio.md)を使用して、検索構文をカスタマイズします。

> [!TIP]
> [[検索/コマンド]](../ide/find-command-box.md) ボックスは、ツール バー コントロールとして使用できますが、既定では表示されません。 **[検索/コマンド]** ボックスを表示するには、**[標準]** ツール バーの **[ボタンの追加または削除]** を選択し、**[検索]** を選択します。

## <a name="find-and-replace-control"></a>[検索と置換] コントロール

**[検索と置換]** コントロールは、コード エディター ウィンドウの右上隅に表示されます。 **[検索と置換]** コントロールにより、現在のドキュメントに出現する指定された検索文字列がすべて直ちに強調表示されます。 検索コントロールの **[次を検索]** または **[前を検索]** をクリックすると、1 つの出現箇所から別の出現箇所に移動できます。

![[検索と置換] コントロール](media/find-and-replace-box.png)

**[検索]** ボックスの横にあるボタンをクリックして、置換オプションにアクセスすることもできます。 置換を 1 か所ずつ実行するには、**[置換]** ボックスの横にある **[次を置換]** をクリックします。 すべての一致項目を置換するには、**[すべて置換]** をクリックします。

一致項目の強調表示色を変更するには、**[ツール]** メニューで **[オプション]**、**[環境]**、**[フォントおよび色]** の順にクリックします。 **[設定の表示]** の一覧で **[テキスト エディター]** をクリックし、**[表示項目]** の一覧で **[蛍光ペンの検索]** (拡張機能) をクリックします。

### <a name="search-tool-windows"></a>ツール ウィンドウでの検索

**[検索]** コントロールは、**[出力]** ウィンドウや **[検索結果]** ウィンドウなどのコード ウィンドウまたはテキスト ウィンドウでも使用できます。これには、**[編集]** > **[検索と置換]** を選択するか、**Ctrl + F** キーを押します。

一部のツール ウィンドウで使用できるバージョンの **[検索]** コントロールもあります。 たとえば、検索ボックスにテキストを入力することにより、**[ツールボックス]** ウィンドウに表示されるコントロールの一覧をフィルター処理できます。 コンテンツを検索できる他のツール ウィンドウとしては、**ソリューション エクスプローラー**、**[プロパティ]** ウィンドウ、**チーム エクスプローラー**などがあります。

## <a name="find-in-files-and-replace-in-files"></a>[フォルダーを指定して検索] と [フォルダーを指定して置換]

**[フォルダーを指定して検索]/[フォルダーを指定して置換]** は **[検索と置換]** コントロールと同様に動作します。ただし、検索のスコープを定義できる点が異なります。 エディター内で開いているファイルを検索するだけでなく、開いているすべてのドキュメント、ソリューション全体、現在のプロジェクト、および選択したフォルダー セットも対象にして検索できます。 また、ファイル名拡張子によって検索することもできます。 **[フォルダーを指定して検索]/[フォルダーを指定して置換]** ダイアログ ボックスにアクセスするには、**[編集]** メニューの **[検索と置換]** を選択するか、**Ctrl + Shift + F** キーを押します。

![[ファイルから検索] ダイアログ ボックス](media/find-in-files-box.png)

### <a name="find-results"></a>検索結果

**[すべて検索]** を選択すると、**[検索結果]** ウィンドウが開き、検索に対する一致項目が一覧表示されます。 一覧内でいずれかの検索結果を選択すると、関連付けられたファイルが表示され、一致項目が強調表示されます。 まだファイルが編集用に開いていなければ、タブ ウェルの右側にあるプレビュー タブで開かれます。 **[検索結果]** ボックスの一覧内の検索にも **[検索]** コントロールを使用できます。

### <a name="create-custom-search-folder-sets"></a>カスタムの検索フォルダー セットの作成

**[検索対象]** ボックスの横にある **[検索フォルダーの選択]** ボタン (**[...]**) をクリックすると、検索スコープを定義できます。 **[検索フォルダーの選択]** ダイアログ ボックスでは、検索対象としてフォルダーのセットを指定し、その指定内容を後で再利用できるように保存することができます。

> [!TIP]
> リモート マシンのドライブをローカル コンピューターにマップした場合、リモート マシン上で検索するフォルダーを指定できます。

### <a name="create-custom-component-sets"></a>カスタムのコンポーネント セットの作成

**[検索対象]** ボックスの横にある **[カスタム コンポーネント セットの編集]** をクリックすると、コンポーネント セットを検索スコープとして定義できます。 インストールされている .NET または COM コンポーネント、ソリューションに含まれている Visual Studio プロジェクト、または任意のアセンブリやタイプ ライブラリ (*.dll*、*.tlb*、*.olb*、*.exe*、*.ocx*) を指定できます。 参照を検索するには、**[参照内で検索]** チェック ボックスをオンにします。

## <a name="see-also"></a>関連項目

- [Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)
- [Visual Studio でのコードのリファクタリング](../ide/refactoring-in-visual-studio.md)