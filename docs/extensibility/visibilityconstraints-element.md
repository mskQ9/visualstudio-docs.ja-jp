---
title: VisibilityConstraints 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f81ddd40a6de287fb40840c0473e5702d385793d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138312"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints 要素
VisibilityConstraints 要素では、コマンドやツールバーのグループの静的な可視性を判断します。 可視性がによって制御される最初の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage を読み込むことがなく、統合開発環境 (IDE) です。  
  
## <a name="syntax"></a>構文  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VisibilityItem 要素](../extensibility/visibilityitem-element.md)|コマンドおよびツールバーの静的な可視性を判断します。|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|コマンドおよびツールバーのグループの静的な可視性を判断します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|IDE に VSPackage を提供するコマンド (たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックスなど) を表すすべての要素を定義します。|  
  
## <a name="example"></a>例  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>関連項目  
 [VisibilityItem 要素](../extensibility/visibilityitem-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)