---
title: '方法: プログラムによって文書を印刷 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a5364bd2cf0f0ea6d5e7ceb7c8a427c5aea301d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-documents"></a>方法: プログラムによって文書を印刷する
  Microsoft Office Word ドキュメントの全体または一部を既定のプリンターに印刷できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>ドキュメント レベルのカスタマイズの一部である文書の印刷  
  
#### <a name="to-print-the-entire-document"></a>文書全体を印刷するには  
  
1.  文書全体を印刷するには、プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> クラスの `ThisDocument` メソッドを呼び出します。 このコード例を使用するには、 `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>文書の現在のページを印刷するには  
  
1.  プロジェクトの <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> クラスの `ThisDocument` メソッドを呼び出し、現在のページを一部印刷することを指定します。 このコード例を使用するには、 `ThisDocument` クラスから実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>VSTO アドインを使用した文書の印刷  
  
#### <a name="to-print-an-entire-document"></a>文書全体を印刷するには  
  
1.  印刷する <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Document> メソッドを呼び出します。 アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>文書の現在のページを印刷するには  
  
1.  印刷する <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Document> メソッドを呼び出し、現在のページを一部印刷することを指定します。 アクティブ文書を印刷するコード例を次に示します。 この例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  