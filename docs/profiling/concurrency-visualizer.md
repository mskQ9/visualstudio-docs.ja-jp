---
title: 同時実行ビジュアライザー | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5adb5f5177afc59f560a988f9c86e1ebbede759
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691226"
---
# <a name="concurrency-visualizer"></a>同時実行ビジュアライザー
> [!NOTE]
>  同時実行ビジュアライザーは、Visual Studio に対する任意の拡張機能です。 同時実行ビジュアライザーと同時実行ビジュアライザー コレクション ツールは、以下のリンクからダウンロードします。  
>   
>  -   [Visual Studio 2017 用同時実行ビジュアライザー](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview)拡張機能をダウンロードします。  
>  -   [Visual Studio 2015 用同時実行ビジュアライザー](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9)拡張機能をダウンロードします。  
> -   [Concurrency Visualizer Collection Tools for Visual Studio 2015](http://www.microsoft.com/en-in/download/details.aspx?id=49103)をダウンロードします。  
>   
>      [同時実行ビジュアライザーのコマンド ライン ユーティリティ (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) を使用して、コマンド ラインからトレースを収集することで、Visual Studio 2015 用の同時実行ビジュアライザーでトレースを表示できます。 このツールは、Visual Studio がインストールされていないコンピューターで使用できます。  
  
 同時実行ビジュアライザーを使用すると、マルチスレッド アプリがどのように動作するかを確認することができます。 同時実行ビジュアライザーのビューには、プログラム内のスレッドとシステム間の時間的な関係をまとめて示す、グラフィカルな表形式のテキスト データが表示されます。 同時実行ビジュアライザーを使用すると、パフォーマンスのボトルネック、十分に活用されていない CPU、スレッドの競合、コア間のスレッドの移行、同期の遅延、DirectX のアクティビティ、重複 I/O の領域などの情報を検索できます。 これらのビューでは、グラフィカルな出力を呼び出し履歴とソース コードにリンクすることで、アクション可能なデータを使用できるようになります。  

> [!NOTE]
>  同時実行ビジュアライザーでは、Web プロジェクトはサポートされません。  
  
 同時実行ビジュアライザーは、 [Windows イベント トレーシング](http://go.microsoft.com/fwlink/?LinkId=234579) の機能に依存しています。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[使用状況ビュー](../profiling/utilization-view.md)|すべてのプロセッサのシステム アクティビティを表示して分析する方法について説明します。|  
|[スレッド ビュー](../profiling/threads-view-parallel-performance.md)|プログラム内のスレッド間の対話を分析する方法について説明します。|  
|[コア ビュー](../profiling/cores-view.md)|コア間のスレッドの移行を分析する方法について説明します。|  
|[適切に動作しないマルチスレッド アプリケーションの一般的なパターン](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|いくつかの一般的なパターンについて説明し、それらがどのように同時実行ビジュアライザーに表示されるかを示します。|  
|[Visual Studio での並行開発に関するブログ](http://go.microsoft.com/fwlink/?LinkId=235385)|同時実行ビジュアライザーのヒントとベスト プラクティスについて説明します。|  
|[パフォーマンス レポートのビュー](../profiling/performance-report-views.md)|Visual Studio プロファイリング ツールのレポートおよびビューに関するリファレンス情報を提供します。|  
|[同時実行ビジュアライザー SDK](../profiling/concurrency-visualizer-sdk.md)|ソース コードをインストルメント化して同時実行ビジュアライザーに追加情報を表示する方法について説明します。|  
|[同時実行ビジュアライザー コマンドライン ユーティリティ (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|同時実行ビジュアライザーのコマンド ライン ユーティリティ (CVCollectionCmd.exe) を使用して、Visual Studio がインストールされていないコンピューター上でトレースを収集および処理する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のプロファイル](../profiling/index.md)  
 [プロファイリング機能ツアー](../profiling/profiling-feature-tour.md)
