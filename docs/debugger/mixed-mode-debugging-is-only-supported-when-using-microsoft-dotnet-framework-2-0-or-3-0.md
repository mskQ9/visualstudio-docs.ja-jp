---
title: Microsoft .NET Framework 2.0 または 3.0 を使用する場合にのみサポートが混合モード デバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5492c79fa15582c5aeaf9b7794958a37bd569313
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474961"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>混合モード デバッグは、Microsoft .NET Framework 2.0 以上を使用している場合にのみサポートされます
2.0 より前のバージョンの Microsoft .NET Framework では、64 ビット プロセスの混合モード デバッグはサポートされません。 つまり、デバッグ中にマネージ コードからネイティブ コードにステップ インすることや、ネイティブ コードからマネージ コードにステップ インすることはできません。  
  
 この問題を回避するには、次の操作を実行します。  
  
-   Microsoft .NET Framework 2.0 または 3.0 のどちらかを使用するようにプロジェクトを更新する。  
  
-   マネージ コードとネイティブ コードを個別のデバッガー セッション内でデバッグする。  
  
-   次の手順に示すように、混合コードを 32 ビット プロセスとしてデバッグする。  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>オペレーティング システムを 32 ビットに変更するには (Visual Basic または C#)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**ショートカット メニュー。  
  
2.  プロパティ ページ をクリックして、**コンパイル**または**デバッグ** タブ。  
  
3.  をクリックして**プラットフォーム**、し、 **x86**プラットフォームの一覧からです。  
  
     Visual Basic コンパイラおよび C# コンパイラの既定では、どの CPU 上でも実行されるコードが生成されます。 64 ビット コンピューター上では、これらのバイナリは 64 ビット プロセスとして実行されます。 で、32 ビット プロセスを実行する必要がありますを選択する**Win32**ではなく、 **AnyCPU**です。  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>オペレーティング システムを 32 ビットに変更するには (C/C++)  
  
1.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**ショートカット メニュー。  
  
     プロパティ ページで、をクリックして**プラットフォーム**、し、 **Win32**プラットフォームの一覧からです。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照してください[SQL デバッグ セットアップ](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)です。  
  
## <a name="see-also"></a>関連項目  
 [64 ビット アプリケーションをデバッグする](../debugger/debug-64-bit-applications.md)