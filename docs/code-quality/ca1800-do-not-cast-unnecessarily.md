---
title: 'CA1800: 不必要にキャストしません'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 34c03adb8ff34d3590ed93264d77536c4cdff080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915570"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: 不必要にキャストしません
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
メソッドは、その引数やローカル変数のいずれかで二重のキャストを実行します。

このルールによって完全な分析のため、デバッグ情報を使用して、テスト対象のアセンブリをビルドする必要があり、関連付けられているプログラム データベース (.pdb) ファイルを使用する必要があります。

## <a name="rule-description"></a>規則の説明
二重のキャストがあるとパフォーマンスが低下します。特に、小さな繰り返しステートメントでキャストが実行される場合はそうです。 明示的な重複するキャスト操作の場合は、キャストの結果、ローカル変数に格納して重複するキャスト演算ではなく、ローカル変数を使用します。

場合は、c#`is`演算子を使用して、実際のキャストが実行される前に、キャストが成功するかどうかをテストの結果をテストしてください、`as`演算子代わりにします。 これにより、暗黙的なキャスト操作によって実行されることがなく、同じ機能、`is`演算子。 または、c# 7.0 以降では、使用、`is`演算子[パターンに一致する](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)型変換をチェックし、1 つの手順でその型の変数に式をキャストします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、キャスト操作の数を最小限に抑えるメソッドの実装を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 パフォーマンス問題がない場合、この規則による警告を抑制するか、完全には、ルールを無視するも安全です。

## <a name="examples"></a>使用例
 次の例は、c# を使用して、規則に違反するメソッド`is`演算子。 2 番目のメソッドに置き換えることで、規則に適合、 `is` 、テストの結果に対して指定された演算子は、`as`演算子で、2 つのイテレーションごとのキャスト操作の数が減少します。 3 番目のメソッドを使用して、規則に適合も`is`で[パターン マッチ](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)型変換が成功した場合は、目的の型の変数を作成します。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 次の例では、メソッド、 `start_Click`、ルール、およびメソッドに違反して複数の重複する明示的なキャストを持つ`reset_Click`キャストをローカル変数に格納することによって、規則に適合します。

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>関連項目
[(c# リファレンス) として](/dotnet/csharp/language-reference/keywords/as)
[が (c# リファレンス)](/dotnet/csharp/language-reference/keywords/is)