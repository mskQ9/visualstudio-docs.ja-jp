---
title: ソース コントロールの VSPackage の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8eb34efef22510d1d8f83590a6bdb7960d70ce49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128946"
---
# <a name="creating-a-source-control-vspackage"></a>ソース コントロールの VSPackage の作成
このドキュメントには、統合されたソース管理パッケージのアーキテクチャの概要へのリンクが含まれています[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、実装するインターフェイスとを使用するサービスで定義されている API と簡単なソースを示すサンプル。パッケージの実装を制御します。  
  
 ソース管理で VSPackage をソース管理と統合するための緊密な統合パスを作成できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 これにより、パッケージを既定のソース管理でホストされている UI をバイパスする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクト システムからのソース制御要求に応答、および対話[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]などのコンポーネント**ソリューション エクスプ ローラー**です。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]支援[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と統合できる VSPackage を作成するメカニズムと提携して[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]サービス モデルを使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 ソース管理プラグインでソース管理機能を実装するために代わるより高度な手段であるソース管理パッケージについて説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [アーキテクチャ](../../extensibility/internals/source-control-vspackage-architecture.md)  
 ダイアグラムを表示し、ソース管理パッケージのコンポーネントについて説明します。  
  
 [機能](../../extensibility/internals/source-control-vspackage-features.md)  
 ソース管理パッケージのさまざまな機能をについて説明します。  
  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 ソース管理パッケージを緊密な統合を実装する必要があります、VSPackage の構造について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理機能を提供するソース管理プラグインを作成する方法について説明します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース制御ユーザー インターフェイス (UI)。  
  
 [ソース管理](../../extensibility/internals/source-control.md)  
 統合の機能としてソース管理を実装するためのオプションについて説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。