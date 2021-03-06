---
title: XDCMake タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dab82b3ddf2bc39d1253321a335e1fe838235819
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572323"
---
# <a name="xdcmake-task"></a>XDCMake タスク
XML ドキュメント ツール (xdcmake.exe) をラップします。このツールは、XML ドキュメント コメント (.xdc) ファイルを .xml ファイルにマージします。  
  
 Visual C++ ソース コードにドキュメンテーション コメントを記入し、[/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) コンパイラ オプションでコンパイルすると、.xdc ファイルが作成されます。 詳細については、[XDCMake リファレンス](/cpp/ide/xdcmake-reference)、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)、xdcmake.exe のコマンドライン ヘルプ オプション (**/?**) をご覧ください。  
  
## <a name="remarks"></a>コメント  
 既定では、xdcmake.exe ツールはいくつかのコマンドライン オプションをサポートしています。 **/old** コマンドライン オプションを指定すると、追加のオプションがサポートされます。  
  
## <a name="parameters"></a>パラメーター  
 **XDCMake** タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|省略可能な **String[]** 型のパラメーターです。<br /><br /> 結合する追加の .xdc ファイルを 1 つまたは複数指定します。<br /><br /> 詳細については、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)の**追加のドキュメント ファイル**に関する説明をご覧ください。 xdcmake.exe については、コマンドライン オプションの **/old** と **/Fs** も参照してください。|  
|**AdditionalOptions**|省略可能な **String** 型のパラメーターです。<br /><br /> コマンド ラインで指定するオプションのリストです。 たとえば、"*/option1 /option2 /option#*" のような形式です。 他の **XDCMake** タスク パラメーターでは表されないオプションを指定する場合は、このパラメーターを使用します。<br /><br /> 詳細については、[XDCMake リファレンス](/cpp/ide/xdcmake-reference)、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)、xdcmake.exe のコマンドライン ヘルプ (**/?**) をご覧ください。|  
|**DocumentLibraryDependencies**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` と現在のプロジェクトがソリューションのスタティック ライブラリ (.lib) プロジェクトに依存している場合、そのライブラリ プロジェクトの .xdc ファイルが現在のプロジェクトの .xml ファイル出力に含まれます。<br /><br /> 詳細については、[XML ドキュメント ジェネレーター プロパティ ページ](/cpp/ide/xml-document-generator-tool-property-pages)の**ドキュメント ライブラリの依存関係**に関する説明をご覧ください。|  
|**OutputFile**|省略可能な **String** 型のパラメーターです。<br /><br /> 既定の出力ファイル名をオーバーライドします。 既定の名前は、処理される最初の .xdc ファイルの名前から派生します。<br /><br /> 詳細については、「[XDCMake リファレンス](/cpp/ide/xdcmake-reference)」の **/out:**`filename` オプションの説明を参照してください。 xdcmake.exe については、コマンドライン オプションの **/old** と **/Fo** も参照してください。|  
|**ProjectName**|省略可能な **String** 型のパラメーターです。<br /><br /> 現在のプロジェクトの名前。|  
|**SlashOld**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、追加の xdcmake.exe オプションを有効にします。<br /><br /> 詳細については、xdcmake.exe の **/old** コマンド ライン オプションを参照してください。|  
|**Sources**|必須の `ITaskItem[]` 型のパラメーターです。<br /><br /> タスクで使用および生成できる MSBuild ソース ファイル アイテムの配列を定義します。|  
|**SuppressStartupBanner**|省略可能な **Boolean** 型のパラメーターです。<br /><br /> `true` の場合、タスクの開始時に著作権およびバージョン番号のメッセージが表示されないようにします。<br /><br /> 詳細については、「[XDCMake リファレンス](/cpp/ide/xdcmake-reference)」の **/nologo** オプションの説明を参照してください。|  
|**TrackerLogDirectory**|省略可能な **String** 型のパラメーターです。<br /><br /> トラッカー ログのディレクトリを指定します。|  
  
## <a name="see-also"></a>参照  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)