---
title: ユーザーへのフィードバック |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3462edb539822cd856cd7281566674b4ed0c4def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548170"
---
# <a name="feedback-to-the-user"></a>ユーザーへのフィードバック
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ユーザーへのフィードバック](https://docs.microsoft.com/visualstudio/extensibility/internals/feedback-to-the-user)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境 (IDE)、視覚的なフィードバック関連の使用可能な機能は、ユーザーの現在の選択と選択のグローバル コンテキストに基づきます。 次の表では、別の選択のコンテキストで使用できる機能を示します。  
  
|選択範囲のコンテキスト|使用可能な機能|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|現在の製品セット|特定の製品|  
|アクティブな階層|階層型の特定|  
|アクティブな階層項目|階層項目の種類固有|  
|アクティブなドキュメント|ドキュメントの種類固有|  
|最上位のマルチ ドキュメント インターフェイス (MDI) ウィンドウ|ウィンドウの種類固有|  
|現在の選択コンテキスト|特定の選択コンテキスト|  
  
 表面化機能をユーザーが必要し、継続的に一貫性のある選択し、環境コンテキスト フィードバックを提供する場合は、IDE で複雑さを軽減します。 IDE のウィンドウが開かれるたびに、次の規則が適用されます。  
  
-   ウィンドウは、その選択コンテキストを変更する場合は、選択のフィードバックが明らかに、ウィンドウに示されているし、ダイナミック ヘルプ ウィンドウは、表示されている場合、現在のコンテキストを反映するように更新されます。  
  
-   ウィンドウは、グローバルの選択コンテキストを変更する場合は、コンテキスト固有のすべてのメニューのアクティブな階層ウィンドウ、およびアプリケーションのタイトル バーが、現在のコンテキストを反映するように更新されます。  
  
-   ウィンドウの現在の選択のプロパティを表面化する必要があります、**プロパティ**ウィンドウし、必要に応じて、表示されている場合、**プロパティ ページ** ダイアログ ボックス。  
  
-   ウィンドウが場合のプロパティを画面またはグローバルの選択コンテキストを変更、選択のフィードバックしないようにしてください ウィンドウで、IDE で作業中のウィンドウでは不要になったときにします。  
  
-   すべてのドキュメントに固有のツール ウィンドウは、アクティブなドキュメントを継続的に反映されます。  
  
-   メニューのツールバー、およびアプリケーションのタイトル バーには、最上位のマルチ ドキュメント インターフェイス (MDI) のクライアント ウィンドウを反映する必要があります。  
  
 たとえば、Visual Basic の Web アプリケーション プロジェクト内の Web フォームの HTML ビューを開くし、ユーザーが選択、`<td>`フィードバックを提供する次のように、タグ。  
  
-   選択範囲のアクティブなウィンドウに示されているし、に反映、**プロパティ**ウィンドウ。  
  
-   ドキュメント固有**ツールボックス**アクティブなドキュメントを反映するように更新されます。  
  
-   **エディター**ツールバーと**テーブル**メニューが表示され、Web フォームのウィンドウを反映するように、タイトル バーを更新します。  
  
-   これは通常、アクティブな階層ウィンドウ**ソリューション エクスプ ローラー**、および現在のコンテキストと、状況依存を反映するように、タイトル バーの更新**プロジェクト**メニュー コマンドがアクティブな Web に適用するようになりましたアプリケーションのプロジェクトです。  
  
## <a name="see-also"></a>関連項目  
 [選択と、IDE で通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)   
 [階層と選択](../../extensibility/internals/hierarchies-and-selection.md)
