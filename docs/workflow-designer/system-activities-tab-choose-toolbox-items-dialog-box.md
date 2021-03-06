---
title: ワークフロー デザイナーのツールボックス項目 ダイアログ ボックスの選択 System.Activities タブ
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82303d173a3d5a066919f8597e4636d63a005f02
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976296"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>[ツールボックス アイテムの選択] ダイアログ ボックスの [System.Activities] タブ

このタブの**ツールボックス アイテムの選択** ダイアログ ボックスでは、Windows Workflow Foundation (WF) 活動、テンプレート、および利用可能なアイテムの一覧を表示します。 この一覧を表示するには選択**ツールボックス アイテムの選択**から、**ツール**メニューを右クリックして、または、**ツールボックス**を選択して**アイテムの選択**を表示する、**ツールボックス アイテムの選択**クリックしてダイアログ ボックスで、その**System.Activities**タブです。既定では、System.Activities、System.ServiceModel.Activities、および System.Activities.Core.Presentation アセンブリ; からワークフロー アクティビティが一覧に含まれますただし、のみ、システム標準アクティビティおよびアクティビティに表示されるその他のアセンブリから追加された、**ツールボックス**が既定でオンです。 最近追加アクティビティが自動的にオンおよびに表示されます、**ツールボックス**をクリックすると**OK**  ダイアログ ボックス。 またでこれらの項目が表示されます、**ツールボックス**アクティビティ、アイテム、テンプレートが存在する名前空間に対応する新しいカテゴリの下。

> [!WARNING]
> ワークフロー アクティビティが含まれていないアセンブリを追加しようとすると、エラー ダイアログが表示され、アセンブリにアクティビティが含まれていないことが示されます。

 このダイアログ ボックスは、プロジェクトに依存し、そのため、 **System.Activities**スタンドアロン XAML または非ワークフロー プロジェクトの種類表示するタブが続行されます。

 フィルター処理はタブごとに行われます。つまり、経由のワークフロー活動を追加することはできません、 **.NET コンポーネント**タブです。追加してその必要がある、 **System.Activities**自体のタブです。

 表示したくないすべての項目をオフにすることができます、**ツールボックス**このダイアログ ボックスからタブ、または別の方法として、実行できます、**削除**コンテキスト メニュー オプションで、**ツールボックス**逆アセンブリを参照しても、元の項目は削除されませんし、**ツールボックス**です。

 アクティビティをデザイナーにドラッグ アンド ドロップしてインスタンス化すると、アイテムを含むアセンブリが参照先のアセンブリ一覧に自動的に追加されます。 アクティビティがアセンブリ C を参照している場合、C は参照先のアセンブリ一覧には追加されません。 アセンブリ C は、GAC、または B. アクティビティと同じディレクトリにある必要があります。スタンドアロンの場合は、アセンブリは GAC または VS のプローブ パスに存在するがします。 この条件を満たしている場合にのみ、ワークフロー デザイナー画面上でアクティビティをドラッグ アンド ドロップできます。

 **ツールボックス**設定は、既定でユーザー オプションとして保存されますので、次回開いたとき、**ツールボックス**、カスタマイズされたワークフロー アクティビティの一覧が表示されます。 この副作用の 1 つに独自のドメイン アイテムを追加している場合、**ツールボックス**を通じて、**ツールボックス アイテムの選択** ダイアログ ボックスを続行して、それらのアイテムで作業しているときに、ワークフロー コンソール アプリケーションもします。 参照したくない場合、コンテキスト メニューを使用してそれらを削除またはを通じてそれをオフに、**ツールボックス アイテムの選択** ダイアログ ボックスの前に説明したようです。

 このダイアログ ボックスの列には、次の情報が表示されます。

 名前

 現在ローカル コンピューターに登録されているワークフロー アクティビティの名前が一覧表示されます。

 Namespace

 アクティビティの構造を定義している .NET Framework クラス ライブラリ名前空間の階層構造が表示されます。

 アセンブリ名

 アクティビティが含まれている .NET Framework アセンブリの名前とバージョンが表示されます。

 ディレクトリ

 ワークフロー アクティビティが含まれている .NET Framework アセンブリの場所が表示されます。 アセンブリはすべて、既定では、グローバル アセンブリ キャッシュにあります。

 コンポーネントの一覧を並べ替えるには、列ヘッダーをクリックします。