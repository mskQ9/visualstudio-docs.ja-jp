---
title: TensorFlow モデルをローカルにトレーニングする
description: AI Tools for Visual Studio でローカルに TensorFlow モデルを実行します
keywords: AI, Visual Studio, TensorFlow, ローカル
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 107145ddc607aeb981797c935a9d693a3fd9f9a6
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
ms.locfileid: "29708934"
---
# <a name="train-a-tensorflow-model-locally"></a>TensorFlow モデルをローカルにトレーニングする

このクイック スタートでは、Visual Studio Tools for AI でローカルに [MNIST](http://yann.lecun.com/exdb/mnist/) データセットを使って TensorFlow モデルをトレーニングします。
MNIST データベースには、60,000 例のトレーニング セットと、手書きの数字の 10,000 例のテスト セットが含まれます。

## <a name="prerequisites"></a>必須コンポーネント

始める前に、次のものがインストールされていることを確認します。

### <a name="google-tensorflow"></a>Google TensorFlow

端末で次のコマンドを実行します。
```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy と SciPy
[NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) と [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy) をインストールします。

### <a name="download-sample-code"></a>サンプル コードをダウンロードする
TensorFlow、CNTK、Theano などでディープ ラーニングを始めるためのサンプルを含むこの [GitHub リポジトリ](https://github.com/Microsoft/samples-for-ai)をダウンロードします。

## <a name="open-solution-and-train-model"></a>ソリューションを開いてモデルをトレーニングする

- Visual Studio を起動し、**[ファイル] > [開く] > [プロジェクト/ソリューション]** の順に選びます。

- ダウンロードしたサンプル リポジトリで **Tensorflow Examples** フォルダーを選び、**TensorflowExamples.sln** ファイルを開きます。

![プロジェクトを開く](media\tensorflow-local\open-project.png)

![ソリューションを開く](media\tensorflow-local\open-solution.png)

- **ソリューション エクスプローラー**で MNIST プロジェクトを探して右クリックし、**[スタートアップ プロジェクトに設定]** を選びます。

- **[開始]** をクリックします。

- 出力がコンソールに表示されます。

![コンソールからの出力例](media\tensorflow-local\console-output.png)

> [!div class="nextstepaction"]
> [クラウドで TensorFlow モデルをトレーニングする](tensorflow-vm.md)