---
title: サードパーティ製の単体テスト フレームワークをインストールする
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d0994b226a80385e381fa7b738c0194ec393d87a
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844696"
---
# <a name="install-third-party-unit-test-frameworks"></a>サードパーティ製の単体テスト フレームワークをインストールする

Visual Studio テスト エクスプ ローラーは、エクスプ ローラーのアダプター インターフェイスを開発した単体テスト フレームワークを実行できます。 フレームワークのインストール プログラムは、バイナリをインストールし、サポートする言語の Visual Studio プロジェクト テンプレートを追加します。 テンプレートを使用してプロジェクトを作成する際、フレームワークはテスト エクスプ ローラーに登録されます。 Visual Studio ソリューションには異なるフレームワークを使用する単体テスト プロジェクトと、異なる言語を対象とした単体テスト プロジェクトを含めることができます。 テスト エクスプ ローラーはそれらすべてを実行します。

## <a name="acquire-third-party-frameworks"></a>サード パーティ製フレームワークを取得する

Visual Studio 拡張機能マネージャーを使用して、または Visual Studio Marketplace から、多くのサードパーティ製の単体テスト フレームワークをダウンロードしてインストールすることができます。 フレームワークは、フレームワークの Web サイトなどの他のサイトからダウンロードすることもできます。

### <a name="install-from-visual-studio"></a>Visual Studio からインストールする

1. [標準] メニューで **[ツール]** をクリックしてから、**[拡張機能と更新プログラム]** をクリックします。

2. **[オンライン]**、**[Visual Studio Marketplace]**、**[ツール]** の順に展開します。 **[テスト]** をクリックします。

3. 一覧を参照してフレームワークを検索します。

4. フレームワークを選択し、**[ダウンロード]** をクリックします。

詳細については、「[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)」を参照してください。

### <a name="install-from-the-web"></a>Web からのインストール

関心のあるフレームワークが分かっている場合は、

1. [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) を開きます。

2. **[検索]** ボックスに、フレームワーク名を入力します。

3. 結果の一覧でフレームワークを選択してから、ツールの Visual Studio Marketplace ページに移動します。

フレームワークの一覧とともにその他のテスト ツールを参照するには、

1. [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) を開きます。

2. **[カテゴリ/コレクションによるフィルター]** で、**[すべて表示]** を選択します。

3. **[カテゴリ]** の一覧 (**[表示中]** というラベルが付けられている) で、**[ツール]** ノードを展開してから、**[テスト]** をクリックします。

4. 結果の一覧でフレームワークを選択してから、ツールの Visual Studio Marketplace ページに移動します。

## <a name="update-to-the-latest-test-adapters"></a>最新のテスト アダプターに更新する

テスト検出と実行のエクスペリエンスを向上させるには、最新の安定したテスト アダプターに更新します。 MSTest、NUnit、および xUnit テスト アダプターへの更新の詳細については、[Visual Studio ブログ](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/)を参照してください。

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>最新の安定したテスト アダプター バージョンに更新するには

1. **[ツール]** > **[NuGet Package Manager]** > **[Manage NuGet Packages for Solution...]** を選択して、ソリューション用の Nuget Package Manager を開きます。

2. **[更新]** タブをクリックし、インストールされている NUnit または xUnit テスト アダプターを検索します。

3. 各テスト アダプターを選択し、ドロップダウン メニューから最新の安定したバージョンを選択します。

4. **[インストール]** ボタンを選択します。

   ![テスト アダプターをアップグレードする](media/install-adapter-upgrade.png)

## <a name="see-also"></a>関連項目

- [コードの単体テスト](../test/unit-test-your-code.md)
