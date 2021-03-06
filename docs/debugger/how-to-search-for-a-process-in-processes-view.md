---
title: '方法: プロセス ビューでのプロセスの検索 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d23199031ce46e57e44a01720493fad4e77c7430
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472479"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>方法: プロセス ビューでプロセスを検索する
検索条件として、プロセス ID またはモジュールの文字列を使用して、[プロセス] ビューで特定のプロセスを検索できます。 検索の最初の方向を指定することもできます。 ダイアログ ボックスで、フィールドは、処理ツリーで選択したプロセスの属性が表示されます。  
  
### <a name="to-search-for-a-process-in-processes-view"></a>プロセス ビューでプロセスを検索するには  
  
1.  ウィンドウを整列するようにその spy++ と、アクティブな[プロセス ビュー](../debugger/processes-view.md)ウィンドウが表示されます。  
  
2.  **検索**] メニューの [選択**プロセスを検索**  
  
     [プロセス検索 ダイアログ ボックス](../debugger/process-search-dialog-box.md)が開きます。  
  
3.  検索条件として、プロセス ID またはモジュールの文字列を入力します。  
  
4.  値を指定しないすべてのフィールドをオフにします。  
  
    > [!TIP]
    >  モジュールが所有するすべてのプロセスを検索するには、クリア、**プロセス**内のモジュール名を入力、**モジュール**ボックス。 使用して**次を検索**プロセスの検索を続行します。  
  
5.  選択**を**または**ダウン**検索の方向。  
  
6.  **[OK]** をクリックします。  
  
 強調表示されて、一致するプロセスが見つかった場合、**プロセス ビュー**ウィンドウです。