---
title: DLL プロジェクトのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5118aafae296d839ad182d51b996da11a6bc556
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057399"
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Visual Studio から DLL プロジェクトのデバッグ
次の Visual Studio テンプレートでは、Dll を作成します。  
  
-   (C++、C#、および Visual Basic) クラス ライブラリ   

-   (C++): Win32 コンソール DLL プロジェクト
  
     詳細については、「 [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md)」を参照してください。

-   (C++、C#、および Visual Basic): Windows フォーム コントロール ライブラリ
  
     Windows フォーム コントロール ライブラリのデバッグは、クラス ライブラリ プロジェクトのデバッグと似ています。 多くの場合、Windows コントロールは別のプロジェクトから呼び出します。 呼び出し元のプロジェクトをデバッグする場合は、Windows コントロールのコードにステップ インし、ブレークポイントを設定し、ほかのデバッグ操作を実行できます。 詳細については、「 [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)」を参照してください。  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 デバッグをどの方法で始める場合でも、DLL のデバッグ バージョンを先にビルドして、アプリケーションが参照する場所にデバッグ バージョンを配置するようにします。 この手順を忘れると、アプリケーションが別のバージョンの DLL を参照して読み込む可能性があります。 その場合、ブレークポイントがヒットせず、プログラムの実行が継続されます。 デバッグ時には、デバッガーの **[モジュール]** ウィンドウを開いて、プログラムが読み込んだ DLL を確認できます。 **[モジュール]** ウィンドウには、デバッグしているプロセスに読み込まれた DLL や EXE が一覧表示されます。 詳細については、「 [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md)」を参照してください。  
 C++ で記述されたコードにデバッガーをアタッチするには、コードが `DebuggableAttribute`を生成する必要があります。 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) リンカー オプションを使ってリンクすると、これを自動的にコードに追加できます。  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 DLL を呼び出す呼び出し元のアプリケーションは、マネージド コードで記述されている場合と、ネイティブ コードで記述されている場合があります。 マネージド DLL とそれを呼び出すネイティブ コードの両方をデバッグする場合は、マネージド デバッガーとネイティブ デバッガーを共に有効にする必要があります。 これを選択することができます、 **\<プロジェクト > プロパティ ページ** ダイアログ ボックスまたはウィンドウ。 DLL プロジェクトからデバッグを開始するか、呼び出し元のアプリケーション プロジェクトからデバッグを開始するかによって、確認方法は異なります。 詳細については、「 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)」を参照してください。  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 プロジェクト テンプレートを使用してコンソール アプリケーション プロジェクトを作成するときは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] により、デバッグ構成とリリース構成に必要な設定が自動的に作成されます。 これらの設定は必要に応じて変更できます。 詳細については、次を参照してください[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)、 [c# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)、 [Visual Basic デバッグ構成のプロジェクトの設定。](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)、および[方法: セット デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)します。  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 このセクションの各プロジェクトでは、DLL を作成します。 DLL は直接実行できず、アプリケーション (通常は EXE) から呼び出す必要があります。 詳細については、「 [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects)」を参照してください。 呼び出し元のアプリケーションは、次の条件のいずれかに該当している場合があります。  
  
-   クラス ライブラリを格納する同じ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内の、別のプロジェクトにビルドされたアプリケーション  
  
-   テスト コンピューターや運用コンピューターに既に配置されている既存のアプリケーション  
  
-   Web に配置され、URL からアクセスするアプリケーション  
  
-   DLL を埋め込む Web ページを含む Web アプリケーション  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
DLL をデバッグするには、まず呼び出し元のアプリケーション (通常、EXE または Web アプリケーション) をデバッグします。 これには、複数の方法があります。  
  
-   呼び出し元のアプリケーションに対するプロジェクトが存在する場合は、そのプロジェクトを開いて、 **[デバッグ]** メニューから実行を開始できます。 詳細については、次を参照してください。[デバッガーの概要](../debugger/getting-started-with-the-debugger.md)します。  
  
-   呼び出し元のアプリケーションが、テスト コンピューターや運用コンピューターに配置されている既存のプログラムであり、既に動作している場合は、それにアタッチできます。 DLL が Internet Explorer によってホストされるコントロール、または Web ページ上のコントロールである場合は、この方法を使用します。 詳細については、「 [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
-   DLL プロジェクトからデバッグできます。 詳細については、「 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)」を参照してください。  
  
-   デバッグすることができます、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [イミディ エイト ウィンドウ](#vxtskdebuggingdllprojectstheimmediatewindow)します。 この場合、 **イミディエイト** ウィンドウは、アプリケーションの役割をします。  
  
呼び出し元のアプリケーションのデバッグを始める前に、通常はクラス ライブラリ内にブレークポイントを設定します。 詳細については、「 [Using Breakpoints](../debugger/using-breakpoints.md)」を参照してください。 ブレークポイントにヒットした場合は、コードのステップ実行により、1 行ずつアクションを確認して問題を特定できます。 詳細については、次を参照してください。[デバッガーでコード内を移動](../debugger/navigating-through-code-with-the-debugger.md)します。
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> [イミディエイト] ウィンドウ  
 DLL の関数やメソッドは、呼び出し元のアプリケーションがなくても評価できます。 そのためには、 **[イミディエイト]** ウィンドウを使用して、デザイン時デバッグを行います。 この方法でデバッグするには、DLL プロジェクトが開いているときに次の手順を実行します。  
  
1.  デバッガーの **[イミディエイト]** ウィンドウを開きます。  
  
2.  `Test` クラスの `Class1`メソッドをテストする場合は、次の C# コードを [イミディエイト] ウィンドウで入力して、 `Class1` 型のオブジェクトをインスタンス化します。 このマネージド コードは、構文を適切に変更することで Visual Basic と C++ で動作します。  
  
    ```cpp
    Class1 obj = new Class1();  
    ```  
  
     C# では、すべての名前を完全修飾する必要があります。 また、メソッドや変数はいずれもデバッグ セッションの現在のスコープとコンテキストに含まれる必要があります。  
  
3.  `Test` が 1 つの `int` パラメーターを受け取るものと想定し、 `Test` [イミディエイト] **ウィンドウを使用して** を評価します。  
  
    ```cpp
    ?obj.Test(10)  
    ```  
  
     結果が **[イミディエイト]** ウィンドウに出力されます。  
  
4.  `Test` の中にブレークポイントを配置し、関数を再び評価してデバッグを継続できます。  
  
    ```cpp
    ?obj.Test(10);  
    ```  
  
     ブレークポイントにヒットすると、 `Test`をステップ実行できます。 `Test`の実行が終了すると、デバッガーはデザイン モードに戻ります。

## <a name="vxtskdebuggingdllprojectsexternal"></a> C++ プロジェクトから外部の DLL をデバッグします。

(コードのステップ) などに使用できるデバッグ機能によって異なりますが、プロジェクトに外部 DLL をデバッグする場合、 [DLL のデバッグ構成](#vxtskdebuggingdllprojectsbuildingadebugversion)がビルドされたかどうかと、 [.pdb ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) DLL に必要なその他のファイルがあるとします。

プロジェクトは、DLL とデバッグに使用される .pdb ファイルを検索できる必要があります。 これらのファイルのコピー先のカスタム ビルド タスクを作成することができます、 **\<プロジェクト フォルダー > \Debug**出力フォルダー、またはファイルを出力フォルダーに手動でコピーできます。

プロパティ ページで、ヘッダー ファイルと *.lib ファイルの場所を簡単に設定できます (C++ プロジェクトを右クリックし、選択**プロパティの表示**を選び、**すべての構成**) をコピーする必要はありませんそれらを出力フォルダーには:

- [C/C++] フォルダー ([全般] カテゴリ) - ヘッダー ファイルを含むフォルダーを指定して、**追加のインクルード ディレクトリ**フィールド。
- [リンカー] フォルダー ([全般] カテゴリ) - .lib ファイルを含むフォルダーを指定して、**追加のライブラリ ディレクトリ**フィールド。 
- [リンカー] フォルダー ([入力] カテゴリ) - で .lib ファイルのファイル名と完全なパスを指定する、**追加の依存関係**フィールド。

構成が正しいから実行を開始してデバッグすること、**デバッグ**メニュー。

プロジェクトの設定の詳細については、次を参照してください。[プロパティ ページ (Visual c)](/cpp/ide/property-pages-visual-cpp)します。
  
## <a name="see-also"></a>関連項目  
 
  [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [Visual C++ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)
