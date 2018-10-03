---
title: 呼び出し元/呼び出し先ビュー - サンプリング データ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ed2f99527b8c1f5f38cbbcfd72ee32ad9912fd3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537811"
---
# <a name="caller--callee-view---sampling-data"></a>呼び出し元/呼び出し先ビュー - サンプリング データ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[呼び出し元/呼び出し先ビュー - サンプリング データ](https://docs.microsoft.com/visualstudio/profiling/caller-callee-view-sampling-data)します。  
  
呼び出し元/呼び出し先ビューには、選択した関数およびその親関数と子関数のプロファイル データが表示されます。 [呼び出し元/呼び出し先] ビューは、3 つのグリッドで構成されます。  
  
 **[現在の関数]** は中央のグリッドに表示されます。このグリッドには、選択した関数に関するプロファイル情報が表示されます。 値には関数のすべてのサンプル呼び出しが含まれます。  
  
 **[現在の関数を呼び出した関数]** は最上部のグリッドに表示されます。このグリッドには、呼び出し元 (親) 関数による、選択した (現在の) 関数の値に対する個別の処理が表示されます。  
  
 **[現在の関数によって呼び出された関数]** は、下部のグリッドに表示されます。このグリッドには、子関数が現在の関数によって呼び出されたときに、選択した関数の呼び出し先 (子) 関数に関するプロファイル情報が表示されます。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 Windows ストア アプリにも新しい収集手法が必要です。 ｢[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
|Column|説明|  
|------------|-----------------|  
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|  
|**プロセス名**|プロセスの名前です。|  
|**モジュール名**|関数を含むモジュールの名前です。|  
|**モジュール パス**|関数を含むモジュールのパスです。|  
|**ソース ファイル**|この関数の定義を含むソース ファイルです。|  
|**関数名**|関数の完全修飾名です。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**関数アドレス**|関数のアドレス。|  
|**Type**|関数のコンテキスト:<br /><br /> -   **0** - 現在の関数<br />-   **1** - 現在の関数を呼び出す関数<br />-   **2** - 現在の関数によって呼び出される関数|  
|**ルート関数名**|現在の関数の名前です。|  
|**サンプル数 (子を含む)**|-   現在の関数の場合、この関数またはその子関数の 1 つを実行中に収集されたサンプルの数。<br />-   呼び出し元関数の場合、この関数が現在の関数を呼び出したときに収集された現在の関数の包括サンプル数。<br />-   呼び出し先関数の場合、現在の関数がこの関数を呼び出したときに収集されたこの関数の包括サンプル数。|  
|**サンプル % (子を含む)**|プロファイル実行のすべてのサンプルに対する、この関数の包括サンプルの割合。|  
|**サンプル数 (関数のみ)**|-   現在の関数の場合、この関数が直接実行されていたとき、つまりこの関数が呼び出し履歴の最上位にあったときに収集されたプロファイル実行のサンプル数。 この関数の子関数の実行中に収集されたサンプルは、排他カウントには含まれません。<br />-   呼び出し元関数の場合、この関数が現在の関数を呼び出したときに収集された現在の関数の排他サンプル数。<br />-   呼び出し先関数の場合、現在の関数がこの関数を呼び出したときに収集されたこの関数の排他サンプル数。|  
|**サンプル % (関数のみ)**|プロファイル実行のすべてのサンプルに対する、この関数の排他サンプルの割合。|  
  
## <a name="see-also"></a>関連項目  
 [呼び出し元/呼び出し先ビュー - .NET メモリ サンプリング データ](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [呼び出し元/呼び出し先ビュー - .NET メモリ インストルメンテーション データ](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [呼び出し元/呼び出し先ビュー - インストルメンテーション データ](../profiling/caller-callee-view-instrumentation-data.md)


