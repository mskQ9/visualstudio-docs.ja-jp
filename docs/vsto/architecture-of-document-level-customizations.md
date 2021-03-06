---
title: ドキュメント レベルのカスタマイズのアーキテクチャ
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 78a00b9d13d93f8ac0fa893e68ca379a7b5f7c3d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="architecture-of-document-level-customizations"></a>ドキュメント レベルのカスタマイズのアーキテクチャ
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Word および Microsoft Office Excel のドキュメント レベルのカスタマイズを作成するためのプロジェクトが含まれています。 ここでは、ドキュメント レベルのカスタマイズの次の側面について説明します。  
  
-   [カスタマイズを理解します。](#UnderstandingCustomizations)  
  
-   [カスタマイズのコンポーネント](#Components)  
  
-   [カスタマイズと Microsoft Office アプリケーションの連携](#HowCustomizationsWork)  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのカスタマイズの作成の概要については、次を参照してください[Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)、 [のWord用ドキュメントレベルのカスタマイズのプログラミングを始める。](../vsto/getting-started-programming-document-level-customizations-for-word.md)、および[Excel 用ドキュメント レベルのカスタマイズのプログラミングを始める](../vsto/getting-started-programming-document-level-customizations-for-excel.md)です。  
  
##  <a name="UnderstandingCustomizations"></a> カスタマイズを理解します。  
 Visual Studio の Office 開発ツールを使用してドキュメント レベルのカスタマイズをビルドする場合は、特定の文書に関連付けられたマネージ コード アセンブリを作成します。 アセンブリがリンクされている文書やブックは、マネージ コード拡張機能がある、と言い表されます。 詳細については、次を参照してください。[デザインおよび Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)です。  
  
 ユーザーがドキュメントを開くと、Microsoft Office アプリケーションによってアセンブリが読み込まれます。 アセンブリが読み込まれると、ドキュメントが開いている間、カスタマイズはイベントに応答できます。 また、ドキュメントが開いている間、カスタマイズはオブジェクト モデルを呼び出し、アプリケーションを自動化して拡張することもできます。 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]内の任意のクラスを使用することも可能です。  
  
 アセンブリは、アプリケーションのプライマリ相互運用機能アセンブリを介してアプリケーションの COM コンポーネントとの通信を行います。 詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)と[Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)です。  
  
 複数のドキュメント レベルのカスタマイズを同時に開くと、各アセンブリは異なるアプリケーション ドメインに読み込まれます。 このため、1 つのソリューションが正しく動作しない場合でも、それが原因で他のソリューションにエラーが発生することはありません。 ドキュメント レベルのカスタマイズは、1 つのアプリケーション ドメイン内の 1 つのドキュメントと連携するように設計されています。 ドキュメント間のやり取りに対応するようには設計されていません。 アプリケーション ドメインの詳細については、次を参照してください。[アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)です。  
  
> [!NOTE]  
>  Visual Studio の Office 開発ツールを使用して作成するドキュメント レベルのカスタマイズは、エンド ユーザーがアプリケーションを起動したときのみ使用されることを目的としています。 アプリケーションがプログラムで起動された場合 (オートメーション機能を使用する場合など)、カスタマイズは予期したとおりに動作しないことがあります。  
  
### <a name="design-time-and-run-time-experiences"></a>デザイン時と実行時のエクスペリエンス  
 ドキュメント レベルのカスタマイズのアーキテクチャを理解すると、ソリューションのデザイン時と実行時におけるエクスペリエンスについて理解を深めることができます。  
  
#### <a name="design-time"></a>デザイン時  
 デザイン時のエクスペリエンスには、次のような手順が含まれます。  
  
1.  開発者は、ドキュメント レベルのプロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で作成します。 このプロジェクトには、ドキュメントと、ドキュメントとは分離して実行されるアセンブリが組み込まれます。 ドキュメントは既に存在している (設計者によって作成済み) 場合もあります。また、プロジェクトと共に新しいドキュメントを作成することもできます。  
  
2.  設計者 (プロジェクトを作成する開発者、または他のユーザーのいずれか) は、エンド ユーザー向けにドキュメントの最終的な外観を仕上げます。  
  
#### <a name="runtime"></a>ランタイム  
 実行時のエクスペリエンスには、次のような手順が含まれます。  
  
1.  エンド ユーザーが、マネージ コード拡張機能を実装している文書またはブックを開きます。  
  
2.  文書またはブックにより、コンパイルされたアセンブリが読み込まれます。  
  
3.  ユーザーが文書またはブックで操作すると、アセンブリがイベントに応答します。  
  
#### <a name="developer-and-end-user-perspective-compared"></a>開発者とエンドユーザーの立場の違い  
 開発者は主に [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で作業を行い、エンド ユーザーは Word または Excel で作業を行うため、ドキュメント レベルのカスタマイズを理解するには、次に示す 2 つの視点に立つことが必要です。  
  
|開発者の視点|エンド ユーザーの視点|  
|-----------------------------|----------------------------|  
|開発者は [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を使用して、Word および Excel にアクセス可能なコードを記述します。<br /><br /> Word または Excel を実行する実行可能ファイルを作成しているように思えますが、実際の処理は別の方法で行われます。 ドキュメントにはアセンブリが関連付けられており、そのアセンブリへのポインターが含まれています。 ドキュメントを開くと、Word または Excel はアセンブリを検索し、すべてのイベント処理に呼応して動作します。|ソリューションを使用するには、他の Microsoft Office ファイルを開く場合と同様に、文書またはブックを開く (または、テンプレートから新しいドキュメントを作成する) だけです。<br /><br /> アセンブリにより、文書またはブックをカスタマイズできます。たとえば、現在のデータを基に文書やブックを自動生成したり、情報の入力を求めるダイアログ ボックスを表示したりできます。|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズのサポートされているドキュメントの形式  
 カスタマイズ プロジェクトを作成するときには、プロジェクト内で使用するドキュメントの形式を選択できます。 詳細については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
 Excel および Word のドキュメント レベルのカスタマイズで使用可能なドキュメント形式を、次の表に示します。  
  
|Excel|Word|  
|-----------|----------|  
|Excel ブック (*.xlsx*)<br /><br /> Excel マクロ有効ブック (*.xlsm*)<br /><br /> Excel バイナリ ブック (*.xlsb*)<br /><br /> Excel 97-2003 ブック (*.xls*)<br /><br /> Excel テンプレート (*.xltx*)<br /><br /> Excel マクロ有効テンプレート (*.xltm*)<br /><br /> Excel 97-2003 テンプレート (*.xlt*)|Word 文書 (*.docx*)<br /><br /> Word マクロ有効文書 (*.docm*)<br /><br /> Word 97-2003 文書 (*.doc*)<br /><br /> Word テンプレート (*.dotx*)<br /><br /> Word マクロ有効テンプレート (*.dotm*)<br /><br /> Word 97-2003 テンプレート (*.dot*)|  
  
 サポートされている形式のドキュメントに対してだけ、マネージ コード拡張機能を設計する必要があります。 そうしないと、アプリケーションでドキュメントを開くときに、特定のイベントが発生しない可能性があります。 たとえば、<xref:Microsoft.Office.Tools.Excel.Workbook.Open>または web ページで、Excel XML スプレッドシート形式で保存されたブックでマネージ コード拡張機能を使用するときに、イベントは発生しません (*.htm*です。*.html*) 形式です。  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>.Xml ファイル名拡張子を持つ Word 文書のサポート  
 ドキュメント レベルのプロジェクト テンプレートを使用して、次のファイル形式に基づくプロジェクトを作成することはできません。  
  
-   Word XML 文書 (*\*xml*)。  
  
-   Word 2003 XML 文書 (*\*xml*)。  
  
 エンド ユーザーがこれらのファイル形式でカスタマイズを使用できるようにするには、前の表に示した、サポートされているいずれかのファイル形式に基づくカスタマイズを作成して配置します。 カスタマイズをインストールすると、エンドユーザーは、Word XML ドキュメントのドキュメントを保存できます (*\*xml*) 形式または Word 2003 XML 文書 (*\*xml*) 形式、およびカスタマイズは、期待どおりに動作し続けます。  
  
##  <a name="Components"></a> カスタマイズのコンポーネント  
 カスタマイズの主要なコンポーネントは、ドキュメントとアセンブリです。 これらのコンポーネントに加えて、Microsoft Office アプリケーションがカスタマイズを検出して読み込むときに重要な役割を果たすものがあります。  
  
### <a name="deployment-manifest-and-application-manifest"></a>配置マニフェストとアプリケーション マニフェスト  
 カスタマイズは、配置マニフェストとアプリケーション マニフェストを使用して、最新バージョンのカスタマイズ アセンブリを特定し、読み込みます。 配置マニフェストは、最新のアプリケーション マニフェストを指します。 アプリケーション マニフェストは、カスタマイズ アセンブリを指し、エントリ ポイント クラス (1 つまたは複数のクラス) を指定して、アセンブリ内で実行します。 詳細については、次を参照してください。[アプリケーション マニフェストおよび配置マニフェスト Office ソリューションにおける](../vsto/application-and-deployment-manifests-in-office-solutions.md)です。  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイム  
 Visual Studio の Office 開発ツールを使用して作成したドキュメント レベルのカスタマイズを実行するには、エンド ユーザーのコンピューターに [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] がインストールされている必要があります。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、カスタマイズ アセンブリを読み込むアンマネージ コンポーネントが含まれています。また、一連のマネージ アセンブリも含まれています。 これらのマネージ アセンブリにより、カスタマイズ コードがホスト アプリケーションを自動化して拡張するために使用するオブジェクト モデルが提供されます。  
  
 詳細については、次を参照してください。 [Visual Studio tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
##  <a name="HowCustomizationsWork"></a> カスタマイズと Microsoft Office アプリケーションとの連携  
 ユーザーが Microsoft Office カスタマイズの一部であるドキュメントを開くと、アプリケーションはそのドキュメントにリンクされている配置マニフェストを使用して、最新バージョンのカスタマイズ アセンブリを特定し、読み込みます。 配置マニフェストの場所がという名前のカスタム ドキュメント プロパティに格納されている**AssemblyLocation**です。 この場所を示す文字列は、ソリューションをビルドするときにプロパティに挿入されます。  
  
 配置マニフェストはアプリケーション マニフェストを指し、アプリケーション マニフェストは最新のアセンブリを指します。 詳細については、次を参照してください。[アプリケーション マニフェストおよび配置マニフェスト Office ソリューションにおける](../vsto/application-and-deployment-manifests-in-office-solutions.md)です。  
  
 ドキュメント レベルのカスタマイズに関する基本アーキテクチャを、次の図に示します。  
  
 ![2007 office カスタマイズ アーキテクチャ](../vsto/media/office07-custom.png "2007 Office カスタマイズ アーキテクチャ")  
  
> [!NOTE]  
>  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とする Office ソリューションでは、ソリューションはプライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を直接呼び出す代わりに、ソリューション アセンブリに埋め込まれた PIA 型情報を使用してホスト アプリケーションのオブジェクト モデルを呼び出します。 詳細については、次を参照してください。[デザインおよび Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)です。  
  
### <a name="loading-process"></a>読み込みプロセス  
 ユーザーが Microsoft Office ソリューションの一部であるドキュメントを開くと、次の処理が実行されます。  
  
1.  Microsoft Office アプリケーションはカスタム ドキュメント プロパティをチェックして、そのドキュメントに関連付けられているマネージ コード拡張機能があるかどうかを調べます。 詳細については、次を参照してください。[カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)です。  
  
2.  マネージ コード拡張機能がある場合、アプリケーションを読み込みます*VSTOEE.dll*、どのロード*VSTOLoader.dll*です。 これらは管理対象ではありません、Visual Studio 2010 Tools for Office runtime のローダー コンポーネントである Dll です。 詳細については、次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
3.  *VSTOLoader.dll*読み込みます、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]のマネージ部分を起動し、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。  
  
4.  ドキュメントがローカル コンピューター以外の場所から開かれている場合、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、該当する Office アプリケーション用に設定された **[セキュリティ センターの設定]** の **[信頼できる場所]** の一覧にドキュメントの場所が載っていることを確認します。 ドキュメントの場所が信頼できる場所でない場合、カスタマイズは信頼されず、読み込みプロセスはここで停止します。  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、ソリューションをインストールし (まだインストールされていない場合)、最新のアプリケーション マニフェストと配置マニフェストをダウンロードし、一連のセキュリティ チェックを実行します。 詳細については、次を参照してください。[セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)です。  
  
6.  カスタマイズを信頼して実行できる場合、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は配置マニフェストとアプリケーション マニフェストを使用して、アセンブリの更新をチェックします。 利用できる新しいバージョンのアセンブリが存在する場合、ランタイムは、クライアント コンピューターの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] キャッシュに新しいバージョンのアセンブリをダウンロードします。 詳細については、次を参照してください。 [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)です。  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、カスタマイズ アセンブリを読み込むときに使用する、新しいアプリケーション ドメインを作成します。  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、カスタマイズ アセンブリをアプリケーション ドメインに読み込みます。  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]呼び出し、**スタートアップ**カスタマイズ アセンブリ内のイベント ハンドラー。 詳細については、次を参照してください[Office プロジェクトのイベント。](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [ビジュアルの Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)   
 [カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)   
 [ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)  
  
  