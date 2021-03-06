---
title: Visual Studio のオフライン インストールを作成する
description: Visual Studio をオフラインでインストールする方法について説明します。
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ef917b4e8aa5cde8d95c036523bb525799cc19e
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36279964"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Visual Studio 2017 のオフライン インストールを作成する

Visual Studio 2017 インストーラーは、さまざまなネットワーク環境またはさまざまなコンピューター環境で問題なく動作するように設計されています。

- 新しいワークロード ベース モデルでは、旧バージョンの Visual Studio よりダウンロード量が少なくなります (最小インストールではわずか 300 MB で済みます)。
- 汎用の "ISO" または zip ファイルと違い、コンピューターに必要なパッケージしかダウンロードしません。 たとえば、不要な場合には 64 ビット ファイルをダウンロードしません。
- インストール プロセス中、アンチウイルス/プロキシ ソフトウェアによる干渉を最小限に抑えるために、3 つの異なるダウンロード技術 (WebClient、BITS、WinInet) が試されます。
- Visual Studio のインストールに必要なファイルはグローバル配信ネットワークで配信されます。そのため、ローカル サーバーから届けられます。

[Visual Studio Web インストーラー](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)をお試しください&mdash;その利便性を実感していただけるものと考えております。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

インターネット接続が利用できないか、信頼性が低いためにオフラインでインストールする場合、「[低帯域幅または信頼性の低いネットワーク環境に Visual Studio 2017 をインストールする](../install/install-vs-inconsistent-quality-network.md)」をご覧ください。 コマンド ラインを利用してオフライン インストールの完了に必要なファイルのローカル キャッシュを作成できます。 このプロセスは以前のバージョンで利用できた ISO ファイルに置き換わるものです。

> [!NOTE]
> 企業の IT 管理者が、インターネットからファイアウォールで隔てられたクライアント ワークステーションのネットワークに Visual Studio 2017 を展開する場合は、「[Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)」と「[Visual Studio オフライン インストールに必要な証明書をインストールする](../install/install-certificates-for-visual-studio-offline.md)」をご覧ください。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://visualstudio.microsoft.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。
