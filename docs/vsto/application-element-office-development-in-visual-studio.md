---
title: '&lt;アプリケーション&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 90810bf6e9a3b47148598c3e9c3d217989f115ea
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;アプリケーション&gt;要素 (Visual Studio での Office 開発)
  `application` 名前空間の `vstav3` 要素は、Office ソリューションの説明をラップします。 ドキュメント レベルのカスタマイズと VSTO アドインでは、子要素が異なります。  
  
## <a name="syntax-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズの構文  
  
```  
<application>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</application>  
```  
  
## <a name="syntax-for-application-level-add-ins"></a>アプリケーション レベルのアドインの構文  
  
```  
<application>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</application>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `application` 名前空間の `vstav3` 要素は、 `vstov4` 名前空間に格納されている、カスタマイズに固有のすべての情報をラップするノードです。  
  
 `application` 要素には属性がありません。  
  
 `application` 要素には、次のような要素があります。  
  
### <a name="customization"></a>カスタマイズ  
 役割、`customization`内の要素、`vstov3`で名前空間が定義されている[&#60;カスタマイズ&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/customization-element-office-development-in-visual-studio.md)です。  
  
## <a name="document-level-customization-example"></a>ドキュメント レベルのカスタマイズの例  
  
### <a name="description"></a>説明  
 次のコード例は `application` を使用して配置されるドキュメント レベルの Office ソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:document   
        solutionId="73e" />  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="vsto-add-in-example"></a>VSTO アドインの例  
  
### <a name="description"></a>説明  
 次のコード例は `application` を使用して配置されるアプリケーション レベルの Office ソリューションの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]要素を示しています。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:application>  
  <vstov4:customizations   
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
    <vstov4:customization>  
      <vstov4:appAddIn   
        application="Outlook"   
        loadBehavior="3"   
        keyName="ContosoOutlookAddIn">  
        <vstov4:friendlyName>  
          ContosoOutlookAddIn  
        </vstov4:friendlyName>  
        <vstov4:description>  
          ContosoOutlookAddIn - Outlook VSTO Add-in   
          created with Visual Studio Tools for Office  
        </vstov4:description>  
        <vstov4:formRegions>  
          <vstov4:formRegion  
              name="OutlookAddIn1.FormRegion1">  
            <vstov4:messageClass name="IPM.Note" />  
            <vstov4:messageClass name="IPM.Contact" />  
            <vstov4:messageClass name="IPM.Appointment" />  
          </vstov4:formRegion>  
        </vstov4:formRegions>  
      </vstov4:appAddIn>  
    </vstov4:customization>  
  </vstov4:customizations>  
</vstav3:application>  
```  
  
## <a name="see-also"></a>関連項目  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  