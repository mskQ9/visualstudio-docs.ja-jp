---
title: 'チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cca12f7c04b51bcf2b695e00d9305a7feb72ebc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144896"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク
独自のコンテンツの種類を定義し、エディターの Managed Extensibility Framework (MEF) 拡張機能を使用して、ファイル名拡張子をリンクできます。 場合によっては、ファイル名拡張子が既に定義されている言語サービス; でただし、MEF で使用するもする必要がありますにリンクするコンテンツの種類。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`ContentTypeTest`です。  
  
2.  **Source.extension.vsixmanifest**ファイルに移動して、**資産**タブをクリックし、設定、**型**フィールドを **[microsoft.visualstudio.mefcomponent]**、**ソース**フィールドを**現在のソリューション内のプロジェクト**、および**プロジェクト**フィールドをプロジェクトの名前。  
  
## <a name="defining-the-content-type"></a>コンテンツの種類を定義します。  
  
1.  クラス ファイルを追加し、名前を付けます`FileAndContentTypes`です。  
  
2.  次のアセンブリへの参照を追加します。  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  次の追加`using`ディレクティブです。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  定義を格納する静的クラスを宣言します。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  このクラスでは、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "hid"という名前し、"text"を使用する基本定義を宣言します。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>コンテンツの種類に、ファイル名拡張子をリンク  
  
-   ファイル名拡張子には、このコンテンツの種類をマップするには、エクスポート、 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> ".hid"を拡張機能を持つし、コンテンツの種類"hid"です。  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>エディターでは、エクスポートするコンテンツの種類を追加します。  
  
1.  エディターの拡張機能を作成します。 説明されている余白グリフの拡張機能を使用するなど、[チュートリアル: 余白グリフを作成する](../extensibility/walkthrough-creating-a-margin-glyph.md)です。  
  
2.  この手順で定義されているクラスを追加します。  
  
3.  拡張機能クラスをエクスポートするときに追加、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>に"hid"型のです。  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)