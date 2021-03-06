---
title: IDE 定数 |Microsoft ドキュメント
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9c7e870b02dbe5a903ca8195954ffd5a8f63549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133114"
---
# <a name="ide-constants"></a>IDE 定数

<xref:Microsoft.VisualStudio.VSConstants>クラスには、統合開発環境 (IDE) に固有とヘッダー ファイル内でだけを以前に定義された定数が用意されています。

## <a name="logical-and-physical-views"></a>論理的および物理的なビュー

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>取得するメソッド、**ファイルを開く**ダイアログ ボックスで、この場合は、選択可能なコード ビューにします。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>取得するメソッド、**ファイルを開く**ダイアログ ボックスで、ここで設定可能な限り<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>デバッグと同じビューにマップされるビュー<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>です。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>取得するメソッド、**ファイルを開く**ダイアログ ボックスで、このようなケースで**フォームの表示**デザイナーのビューです。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>取得するメソッド、**ファイルを開く**ダイアログ ボックスで、この場合、エディター ファクトリの既定/プライマリ ビュー。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>取得するメソッド、**ファイルを開く**ドキュメントまたはデータのテキスト エディターのビューのダイアログ ボックスで、します。|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` ハンドラーは、この値を渡す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを使用するユーザー定義ビューを選択するユーザーの入力を求められる。|

## <a name="editor-factory-flags"></a>エディター ファクトリ Flags

|[値]|説明|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|古いフラグの組み合わせの最初のパラメーターとしてビットごとの<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドです。|
|[CEF です。OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|最初のパラメーターとしてビットごとの<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、これは、かエディター ファクトリに必要な修正を実行する必要があります。|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|最初のパラメーターとしてビットごとの<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドでは、このフラグは相互に exclusive [CEF です。CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)です。|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|最初のパラメーターとしてビットごとの<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッド、これは、かエディター ファクトリは、ユーザー インターフェイス (UI) を表示せず、エディターを作成する必要があります。|

## <a name="visual-studio-errors"></a>Visual Studio のエラー

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|非同期動作をインターフェイスによって返される定数ときに、オブジェクトで該当ビジーです|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|エラーに固有である HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 「互換性のないドキュメント データ」です。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示す「パッケージが読み込まれていません」と|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示すことと、「プロジェクトは既に存在します」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|エラーに固有である HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] "プロジェクト構成に失敗しました"を示すと。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「プロジェクトは読み込まれていません」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示す「ソリューション既に開かれている」と|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「ソリューション開かれていません」。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|配列を指定するためのパラメーターを持つビルド インターフェイスによって返される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput>インターフェイスが実装にのみ適用できるメソッドすべての出力。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>メソッドは、ドキュメントがエディターで開くことができない形式にこの値を返します。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|ユーザーが [戻る] ボタンをヒットすることを示す HRESULT 値、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ウィザード。|

## <a name="visual-studio-constants"></a>Visual Studio の定数

|[値]|説明|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|エラーに固有である HRESULT[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を示し、「プロジェクト」転送します。|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|固有である定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]「ツールボックス マーカー」|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|固有である定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]経由で通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>メソッド モダリティの先頭を示します。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|固有である定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]経由で通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>モダリティの末尾を示す方法。|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|固有である定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]経由で通知メッセージを配信するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A>コマンド バーのメトリックが変更されたことを示すメソッドです。|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|固有である定数[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cookie が設定されていないことを示すです。|
|[VSITEMID です。Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト項目の休暇を表す項目の識別子。 この値は、現在選択されていないときに使用されます。|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト階層のルートを表し、1 つの項目ではなく、階層全体の識別に使用される項目の識別子。|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|A[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]項目識別子を表す、現在選択されている項目が、階層のルートを含めることができます。|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 IDE のコンポーネントだけが選択されている について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>を呼び出すと、例を示します。

|定数|[値]|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 新しい選択状態を示すために使用する定数。

|定数|[値]|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>コンポーネントの選択 ダイアログの定数

|定数|[値]|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>関連項目

- [プロジェクト システムを拡張するための IDE 定義コマンド](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)