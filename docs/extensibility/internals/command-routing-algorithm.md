---
title: コマンド ルーティング アルゴリズム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aba7ddcdda4dd4eabbb9266e0fa89c916bb028f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131497"
---
# <a name="command-routing-algorithm"></a>コマンド ルーティング アルゴリズム
Visual Studio でのコマンドは、さまざまなコンポーネントによって処理されます。 コマンドは、現在の選択に基づいて、最も内側のコンテキストから最も外側の (グローバルとも呼ばれます) のコンテキストにルーティングされます。 詳細については、次を参照してください。[可用性](../../extensibility/internals/command-availability.md)です。  
  
## <a name="order-of-command-resolution"></a>コマンドの解像度の順序  
 コマンドは、レベルは次のコマンド コンテキストを介して渡されます。  
  
1.  アドイン: 環境に存在するすべてのアドイン コマンドが最初に提供します。  
  
2.  コマンドの優先順位: を使用してこれらのコマンドが登録されている<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>です。 Visual Studio で、すべてのコマンドを呼び出して、それらが登録されている順序で呼び出されます。  
  
3.  コンテキスト メニューのコマンド: コンテキスト メニューにあるコマンドが一般的なルーティングするために、コンテキスト メニューにし、その後に提供されるコマンドの対象に提供される最初。  
  
4.  ツールバーがコマンド ターゲットを設定します。 を呼び出すときにこれらのコマンド ターゲットが登録されて<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>です。 `pCmdTarget`パラメーターを指定できます`null`です。 ない場合は`null`を設定して、ツールバー上にあるすべてのコマンドを更新するコマンドは、このターゲットが使用されます。 シェルは、ツールバーを設定するかどうかは、ウィンドウ フレームとして渡す、`pCmdTarget`コマンド、ツールバーを通過ウィンドウ フレームのすべての更新もようにときになっていないフォーカスします。  
  
5.  Tool Window: ツール ウィンドウは、通常を実装している、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスを実装する必要も、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスのツール ウィンドウがアクティブなウィンドウ、Visual Studio は、コマンド ターゲットを取得できます。 ただし、ツール ウィンドウを持つ場合は、フォーカスがある、**プロジェクト**ウィンドウで、次のコマンドにルーティング、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>選択した項目の共通の親であるインターフェイスです。 コマンドをルーティングこの選択は、複数のプロジェクトにまたがっている場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>階層。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスが含まれています、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>に対応するコマンドに似ているメソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。  
  
6.  ドキュメント ウィンドウ: RouteToDocs フラグがその .vsct ファイルで設定をコマンドには、Visual Studio の検索、ドキュメント ビュー オブジェクトに、次のいずれかのコマンドの対象のインスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスまたはドキュメントではオブジェクトのインスタンス (通常、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>インターフェイスまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイス)。 Visual Studio には、コマンドをルーティング ドキュメント ビュー オブジェクトが、コマンドをサポートしていない場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>返されるインターフェイスです。 (これは、ドキュメント データ オブジェクトのオプションのインターフェイスです)。  
  
7.  現在の階層: 現在の階層がアクティブなドキュメント ウィンドウまたはで選択されている階層を所有しているプロジェクトを指定できます**ソリューション エクスプ ローラー**です。 Visual Studio は検索、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>現在、またはアクティブな階層に実装されているインターフェイス。 階層は、プロジェクト項目のドキュメント ウィンドウにフォーカスがある場合でも、階層は、アクティブなときに有効なコマンドをサポートする必要があります。 ただし、コマンドの場合にのみ適用されている**ソリューション エクスプ ローラー**を使用してフォーカスをサポートする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスとその<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>メソッドです。  
  
     **切り取り**、**コピー**、**貼り付け**、**削除**、**の名前を変更**、**入力**、および**DoubleClick**コマンドは、特別な処理を必要とします。 処理する方法については**削除**と**削除**階層では、コマンドを参照してください、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>インターフェイスです。  
  
8.  Global: 場合で、前に説明したコンテキストからコマンドが処理されていない、Visual Studio 試みますを実装するコマンドを所有する VSPackage をルーティングする、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 場合は、VSPackage が既に読み込まれていませんが、それが読み込まれていない Visual Studio を呼び出すと、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドです。 VSPackage にされる場合にのみが読み込まれて、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [コマンド デザイン](../../extensibility/internals/command-design.md)