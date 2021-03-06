---
title: Visual Studio でのコード化された Web パフォーマンス テスト
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 65331aa24eee140bcba983f1360c02f0227905fe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750855"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>コード化された Web パフォーマンス テストの生成と実行

Web パフォーマンス テストは、Web アプリ内を移動することによって記録されます。 これらのテストは、ロード テストに含まれており、複数ユーザーのストレス下で Web アプリケーションのパフォーマンスを測定するために使用されます。 Web パフォーマンス テストは、コード ベースのスクリプトに変換したうえで、他のソース コードと同様に編集およびカスタマイズすることができます。 たとえば、ループ構造と分岐構造を追加できます。

## <a name="generate-a-coded-web-performance-test"></a>コード化された Web パフォーマンス テストを生成する

1.  Web パフォーマンス テストを作成していない場合は、「[Record a web performance test](/vsts/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project)」(Web パフォーマンス テストの記録) を参照してください。

2.  コード化されたテストを生成します。

     ![コード化された Web パフォーマンス テストを生成する](../test/media/web_test_coded_generate.png)

3.  テストの名前を指定します。

     ![コード化された Web パフォーマンス テストの名前を入力する](../test/media/web_test_coded_generate_nametest.png)

     新しいコード化されたテストがコード エディターで開きます。

     ソリューションに、どの Web パフォーマンスおよびロード テスト プロジェクト テンプレートを追加したかによって、コードは Visual Basic または Visual C# のいずれかで生成されます。

     ![コード化された新しいテストがコード エディターで開く](../test/media/web_test_coded_generate_opencodeeditor.png)

     このコードでは、記録されたテストにあった各検証規則と Web 要求が、C# の GetRequestEnumerator() メソッドまたは Visual Basic の Run() メソッドに含まれていることを確認できます。

4.  単純なコードの追加を行います。これには、メソッドの終わりまでスクロール ダウンし、最後の Web 要求のコードの後に、次のコードを追加します。

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("http://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("http://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5.  ソリューションをビルドし、カスタム コードのコンパイルを確認します。

6.  テストを実行します。

     ![コード化された Web パフォーマンス テストの実行](../test/media/web_test_coded_generate_run.png)

     実行日が水曜日であるため、次のようになります。

     ![コード化された Web パフォーマンス テストの結果](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Q&A

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Q: 同時に複数のテストを実行できますか。
 **A:** はい。ソリューション エクスプローラーでコンテキスト メニューを使用してください。

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Q: データ ソースは、コード化されたテストを生成する前か後のどちらに追加すべきでしょうか。
 **A:** [データ ソース](../test/add-a-data-source-to-a-web-performance-test.md)は、コード化されたテストを生成する前に追加する方が簡単です。こうすると、コードが自動的に生成されます。

 データ ソースが含まれるコード化されたテストを実行すると、次のエラー メッセージが表示されることがあります。

 **エージェント \<コンピューター名> でテスト \<テスト名> を実行できません: オブジェクト参照がオブジェクトのインスタンスに設定されていません。**

 これは、テスト クラスに対して DataSourceAttribute が定義されていても、対応する DataBindingAttribute がない場合に発生します。 このエラーを解決するには、適切な DataBindingAttribute を追加して削除するか、コード内でコメント アウトします。

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Q: 検証規則および抽出規則は、コード化されたテストを生成する前か後のどちらに追加すべきでしょうか。
 **A:** 検証規則および抽出規則は、コード化されたテストを生成する前に追加する方が簡単です。ただし検証目的の場合は[コード化された UI テスト](../test/use-ui-automation-to-test-your-code.md)を使用することをお勧めします。