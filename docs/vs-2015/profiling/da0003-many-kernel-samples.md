---
title: 'DA0003: カーネル サンプルが多数存在します | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4412fc120eb0a0fa039ac91bec4da4ba4a6f44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546750"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: カーネル サンプルが多数存在します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DA0003: カーネル サンプルが多数](https://docs.microsoft.com/visualstudio/profiling/da0003-many-kernel-samples)します。  
  
規則 Id |DA0003 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |サンプリング |  
|メッセージ |サンプルの大部分がカーネル モードであります。 これは I/O アクティビティの量が多いか、コンテキスト切り替えの率が高いことを示す可能性があります。 インストルメンテーション モードを使用して、アプリケーションのプロファイリングを検討してください |。  
|規則の種類 |情報 |  
  
## <a name="cause"></a>原因  
 アプリケーションに対して集められた呼び出し履歴の大部分がカーネル モードで実行されています。 別のプロファイリング方法でアプリケーションをプロファイリングすることを検討してください。  
  
## <a name="rule-description"></a>規則の説明  
 Windows の場合、カーネル モードまたはユーザー モードでコードを実行できます。 (カーネル モードは特権モードとも呼ばれています。)デバイス ドライバーなど、低レベルのシステム コードのみカーネル モードで実行されます。 ユーザー モードのアプリケーションは、I/O 操作の実行、スレッドまたはプロセスの同期プリミティブの待機、またはシステム コールを実行するために、カーネル モードに遷移できます。  
  
 サンプリングは、ほとんどの時間をユーザー モードでの作業に費やすアプリケーションのプロファイリングで最も有効です。 アプリケーションがカーネル モードで実行されたときに集められたサンプルの数は、頻繁に発生する I/O 操作を示すか、コンテキスト切り替えが発生していることを示すことがあります。 これらの操作のいずれも、サンプリング方法では調査できません。 カーネル モードで採取されたサンプルが多すぎると、サンプリング データに、統計的な意味を持つだけ十分な数のユーザー モード サンプルが含まれない場合があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 次のいずれかのオプションで再度、アプリケーションをプロファイリングすることを検討してください。  
  
-   インストルメンテーション方式を使用してプロファイリングする。  
  
-   サンプリング レートを増やし、ユーザー モードで集めるサンプルを増やす。


