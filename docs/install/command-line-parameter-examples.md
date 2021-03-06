---
title: Visual Studio のインストールに使用するコマンド ライン パラメーターの例
description: これらの例をカスタマイズして、Visual Studio の独自のコマンド ライン インストールを作成します。
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 829a7892b1d35df2fe5cd2a42dcc431f5ccbb7dc
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36279952"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例

[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)方法を説明するため、いくつかの例を以下に示します。例は必要に応じてカスタマイズできます。

それぞれの例で、`vs_enterprise.exe`、`vs_professional.exe`、`vs_community.exe` は Visual Studio ブートストラップの各エディションを表します。ブートストラップは、ダウンロード プロセスを開始する (約 1 MB の) 小さいファイルです。 別のエディションを使用している場合は、適切なブートス トラップの名前に置き換えてください。

> [!NOTE]
> すべてのコマンドは、管理者特権で実行する必要があり、管理者のプロンプトからプロセスが開始されていない場合は、ユーザー アカウント制御の確認メッセージが表示されます。
>
> [!NOTE]
>  コマンド ラインの末尾で `^` 文字を使用すると、複数行を連結して 1 行にすることができます。 または、これらのコマンドを単純に 1 つの行に配置できます。 PowerShell の場合、バッククォート (`` ` ``) 文字がこれに相当します。

## <a name="using---installpath"></a>Using --installPath

* 対話型プロンプトを使用せず、進行状況を表示して、Visual Studio の最小限のインスタンスをインストールする例です。

 ```cmd
 vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
 ```

* コマンド ラインを使用して Visual Studio インスタンスを更新すると、対話型のプロンプトは表示されませんが、進行状況が表示されます。

 ```cmd
 vs_enterprise.exe --update --quiet --wait
 vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
 ```

 > [!NOTE]
 > 両方のコマンドが必要です。 最初のコマンドにより Visual Studio インストーラーが更新されます。 2 つめのコマンドにより Visual Studio インスタンスが更新されます。 ユーザー アカウント制御ダイアログが表示されないようにするには、管理者としてコマンド プロンプトを実行します。

* フランス語の言語パックを使用する Visual Studio のデスクトップ インスタンスをサイレント モードでインストールする例です。製品のインストールが終わるまでダイアログは表示されません。

 ```cmd
 vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
 ```

 > [!NOTE]
 > `--wait` パラメーターはバッチ ファイル用に設計されています。 バッチ ファイルでは、インストールが完了するまで次のコマンドの実行は続行されません。 `%ERRORLEVEL%` 環境変数にはコマンドの戻り値が格納されます (「[コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)」のページを参照)。

## <a name="using---layout"></a>Using --layout

* Visual Studio コア エディター (最小 Visual Studio 構成) をダウンロードします。 英語の言語パックのみを組み込みます。

 ```cmd
 vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
 ```

* .NET デスクトップおよび .NET Web ワークロード、すべての推奨コンポーネント、GitHub 拡張機能をダウンロードする例です。 英語の言語パックのみを組み込みます。

 ```cmd
 vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
 ```

## <a name="using---includerecommended"></a>Using --includeRecommended

* Visual Studio 2017 Enterprise Edition で利用できるすべてのワークロードとコンポーネントの対話型インストールを開始します。

 ```cmd
 vs_enterprise.exe --all --includeRecommended --includeOptional
 ```

* Visual Studio 2017 Community Edition が既にインストールされているコンピューターに、Visual Studio 2017 Professional の 2 つ目の名前付きインスタンスを Node.js 開発のサポートとともにインストールします。

 ```cmd
 vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
 ```

## <a name="using---remove"></a>Using --remove

* 既定のインストール済み Visual Studio のインスタンスからプロファイリング ツール コンポーネントを削除します。

 ```cmd
 vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
 ```

## <a name="using---path"></a>Using --path

これらのコマンドライン パラメーターは **15.7 の新機能**です。 詳細については、[コマンドライン パラメーターを使用した Visual Studio のインストール](use-command-line-parameters-to-install-visual-studio.md)に関するページをご覧ください。

* install、cache、shared パスを使用:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* install パスと cache パスのみを使用:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* install パスと shared パスのみを使用:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* install パスのみを使用:

 `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://visualstudio.microsoft.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
