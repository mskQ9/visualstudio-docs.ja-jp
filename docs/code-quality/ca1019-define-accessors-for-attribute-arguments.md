---
title: 'CA1019: 属性引数にアクセサーを定義します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbe76788510ebb51c0f6bd609cf91d9791dad2dd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898916"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: 属性引数にアクセサーを定義します
|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 コンス トラクターでは、属性は、対応するプロパティがない引数を定義します。

## <a name="rule-description"></a>規則の説明
 属性では、対象に適用するときに必ず指定する必須の引数を定義できます。 この引数は、コンストラクターに位置指定パラメーターで属性を指定できるようになるため、位置指定引数とも呼ばれます。 必須のすべての引数について、対応する読み取り専用のプロパティも属性で規定する必要があります。これは、引数値を実行時に取得できるようにするためです。 このルールは、各コンス トラクター パラメーターに対応するプロパティを定義したを確認します。

 また、属性ではオプションの引数も定義できます。これは名前付き引数とも呼ばれます。 この引数は、名前でコンストラクターに属性を指定するときに使用されます。また、対応する読み取り/書き込みプロパティが必要です。

 必須およびオプションの引数では、対応するプロパティとコンス トラクターのパラメーターを使用する必要がありますの大文字小文字が異なる同じ名前を付けます。 プロパティは pascal 形式を使用してパラメーターを使用して camel 形式の大文字と小文字と大文字と小文字、します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、各コンス トラクターのパラメーターがない 1 つの読み取り専用プロパティを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 必須の引数を取得できる値したくない場合は、この規則による警告を抑制します。

## <a name="custom-attributes-example"></a>カスタム属性の使用例

### <a name="description"></a>説明
 次の例では、必須 (位置指定) のパラメーターを定義する 2 つの属性を示します。 属性の最初の実装が正しく定義されていません。 2 番目の実装が正しいです。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>位置と名前付き引数

### <a name="description"></a>説明
 オフにすると、属性の必須とする引数は省略可能なライブラリのコンシューマーに位置と名前付き引数を加えます。

 次の例は、位置指定および名前付きの両方の引数を持つ属性の実装を示しています。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

### <a name="comments"></a>コメント
 次の例では、2 つのプロパティにカスタム属性を適用する方法を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>関連規則
 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目
 [属性](/dotnet/standard/design-guidelines/attributes)