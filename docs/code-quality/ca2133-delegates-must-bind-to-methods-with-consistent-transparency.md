---
title: 'CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65fa4c4c6d1d32bceb1bdd9dc0ca63edeab637ff
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179805"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

> [!NOTE]
> この警告は CoreCLR (Silverlight web アプリケーションに固有である CLR のバージョン) を実行しているコードにのみ適用されます。

## <a name="cause"></a>原因

マークされているデリゲートをバインドするメソッドでこの警告が発生した、<xref:System.Security.SecurityCriticalAttribute>透明かでマークされたメソッドに、<xref:System.Security.SecuritySafeCriticalAttribute>します。 この警告は、透過的なデリゲートまたはセーフ クリティカルなデリゲートを、クリティカル メソッドにバインドするメソッドに対しても適用されます。

## <a name="rule-description"></a>規則の説明

デリゲート型と、メソッドにバインドするのには、透過性の整合性がある場合があります。 セーフ クリティカル、透過的なデリゲートは可能性があります他の透過的なまたはセーフ クリティカル メソッドにのみバインド。 同様に、重要なデリゲートでは、重要なメソッドにバインドがのみです。 これらのバインディング規則では、ことをデリゲート経由でのメソッドを呼び出すことができるコードだけでしたがも同じメソッドを直接呼び出すことを確認します。 たとえば、バインディング規則は、透過的なデリゲートを直接使用して重要なコードの呼び出しから透過的なコードを防ぐ。

## <a name="how-to-fix-violations"></a>違反の修正方法

この警告の違反を修正するには、または 2 つの透過性が同等になるように、バインドされているメソッドのデリゲートの透明度を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況

この規則による警告は抑制しないでください。

### <a name="code"></a>コード

[!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]