---
title: Python の概要のチュートリアル、手順 0、インストール
description: Visual Studio で Python を使用するための中核となるチュートリアルの手順 0 (インストールの前提条件)。
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9ce7a388a9cc26ba84796710ff6f94395890a3df
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057649"
---
# <a name="install-python-support-in-visual-studio"></a>Visual Studio での Python サポートのインストール

> [!Note]
> 現在、Python のサポートは Visual Studio for Windows でのみ使用できます。Mac と Linux では、[Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial) を利用して Python のサポートを使うことができます。

1. Windows 用の最新の Visual Studio 2017 インストーラーをダウンロードして実行します (Python のサポートがあるのは、リリース 15.2 以降です)。 Visual Studio が既にインストールされている場合は、Visual Studio インストーラーを実行し、手順 2 へ進みます。

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 のインストールに関するコミュニティ</a>

    >[!Tip]
    > このコミュニティ版は、個人の開発者、クラス学習、学術研究、オープン ソース開発向けです。 その他の用途には、<a target="frameTarget" href="https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Professional</a> または <a target="frameTarget" href="https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted">Visual Studio 2017 Enterprise</a> を使用してください。

1. インストーラーによって、ワークロード一覧が表示されます。これは、特定の開発分野の関連オプションのグループです。 Python の場合、**[Python 開発]** ワークロードを選択し、**[インストール]** を選択します。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](media/installation-python-workload.png)

1. Python のサポートをすばやくテストするには、Visual Studio を起動し、Alt+I キーを押して Python Interactive ウィンドウを開き、`2+2` を入力します。 `4` という出力が表示されない場合は、手順を再確認してください。

    ![対話型ウィンドウでの Python のテスト](media/installation-interactive-test.png)

## <a name="next-step"></a>次のステップ

> [!div class="nextstepaction"]
> [手順 1: Python プロジェクトの作成](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>関連項目

- [既存の Python インタープリターを手動で識別する](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installing-python-support-in-visual-studio.md)
- [インストールする場所](installing-python-support-in-visual-studio.md#install-locations)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
