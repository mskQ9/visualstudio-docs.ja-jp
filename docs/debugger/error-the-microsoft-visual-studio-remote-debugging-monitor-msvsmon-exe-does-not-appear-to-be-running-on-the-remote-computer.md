---
title: 'エラー : Microsoft Visual Studio リモート デバッグ モニター (MSVSMON.EXE) は、リモート コンピューター上では実行されていません。 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 683af8cf0c75068a58b5e8cf4732cdf69c586d4f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476066"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>エラー : Microsoft Visual Studio リモート デバッグ モニター (MSVSMON.EXE) は、リモート コンピューター上では実行されていません。
このエラー メッセージは、Visual Studio がリモート コンピューター上で Visual Studio リモート デバッグ モニターの適切なインスタンスを見つけることができなかったことを示します。 リモート デバッグを行うには、Visual Studio リモート デバッグ モニターをインストールする必要があります。 ダウンロードして、リモート デバッガーの設定については、次を参照してください。[リモート デバッグ](../debugger/remote-debugging.md)です。  
  
> [!IMPORTANT]
>  製品のバグによりこのメッセージが表示されている場合は、次のようにしてください。 [Visual Studio にこの問題を報告](../ide/how-to-report-a-problem-with-visual-studio-2017.md)です。 その他の支援が必要な場合は、Microsoft へのお問い合わせ方法について、「 [Talk to Us](../ide/talk-to-us.md) 」を参照してください。  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Visual Studio 2010 以前でのデバッグ中にこのメッセージが表示される  
 使用している Visual Studio のバージョンが Visual Studio 2010 以前の場合、ファイルとプリンターの共有が有効でないときに、このエラーを受け取る可能性があります。 この問題の詳細についてを参照してください、Visual Studio 2010 バージョンのドキュメント:[エラー: Microsoft Visual Studio リモート デバッグ モニター (MSVSMON です。EXE) は、リモート コンピューター上で実行するのには表示されません。-Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>ローカルでのデバッグ中にこのメッセージが表示される  
 ローカルでのデバッグ中にこのメッセージが表示される場合、ウイルス対策ソフトウェアまたはサード パーティ製のファイアウォールに原因がある可能性があります。 Visual Studio は 32 ビット アプリケーションであるため、リモート デバッガーの 64 ビット バージョンを使用して 64 ビット アプリケーションをデバッグします。 2 つのプロセスは、ローカル コンピューター内のローカル ネットワークを使用して通信します。 コンピューターからトラフィックが送信されることはありませんが、サード パーティのセキュリティ ソフトウェアが通信を妨げる可能性があります。  
  
 次のセクションでは、このメッセージが表示される他のいくつかの理由、および問題を解決するために実行できる事柄について示します。  
  
## <a name="the-remote-machine-is-not-reachable"></a>リモート コンピューターに到達できません  
 リモート コンピューターに [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) してみてください。 Ping に応答がない場合、リモート ツールも接続することはできません。 リモート コンピューターを再起動するか、またはネットワークでリモート コンピューターが正しく構成されていることを確認してください。  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>リモート デバッガーのバージョンは Visual Studio のバージョンと一致しません  
 ローカルで実行している Visual Studio のバージョンは、リモート コンピューターで実行されているリモート デバッグ モニターのバージョンと一致している必要があります。 これを解決するには、リモート デバッグ モニターの一致するバージョンをダウンロードして、インストールします。 [ダウンロード センター](http://www.microsoft.com/en-us/download) に移動して、適切なバージョンのリモート デバッガーを検索します。  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>ローカル コンピューターとリモート コンピューターの認証モードが異なる  
 ローカル コンピューターとリモート コンピューターで、同じ認証モードを使用する必要があります。 これを解決するには、両方のマシンで同じ認証モードを使用するようにします。 認証モードの詳細については、「 [Windows 認証の概要](https://technet.microsoft.com/en-us/library/hh831472.aspx)」を参照してください。  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>異なるユーザー アカウントを使用してリモート デバッガーを実行している  
 これは、次のいずれかの方法で解消できます。  
  
-   リモート デバッガーを停止し、ローカル コンピューターで使用しているアカウントで再起動します。  
  
-   使用してコマンドラインからリモート デバッガーを開始することができます、 **/allow\<ユーザー名 >** パラメーター。 `msvsmon /allow <username@computer>`  
  
-   リモート デバッガーのアクセス許可をユーザーを追加することができます (リモート デバッガー ウィンドウで、**ツール > のアクセス許可**)。  
  
-   前の手順の方法を使用できない場合は、すべてのユーザーにリモート デバッグの実行を許可します。 リモート デバッガー ウィンドウに移動、**ツール > オプション**ダイアログ。 **[認証なし]** を選択すると、 **[すべてのユーザーにデバッグを許可する]** をチェックできるようになります。 ただし、このオプションの使用は、他に選択肢がない場合、またはプライベート ネットワーク上で作業している場合に限る必要があります。  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>リモート コンピューター上のファイアウォールがリモート デバッガーへの着信接続を許可しません  
 Visual Studio とリモート デバッガーの間の通信を許可するように、Visual Studio のコンピューター上のファイアウォールとリモート コンピューター上のファイアウォールを構成する必要があります。 リモート デバッガーが使用するポートについては、「 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)」を参照してください。 Windows ファイアウォールを構成する方法については、「 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)」を参照してください。  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>ウイルス対策ソフトウェアが接続をブロックしている  
 Windows のウイルス対策ソフトウェアがリモート デバッガーの接続を許可しても、その他のサード パーティ製のウイルス対策ソフトウェアがそれらの接続をブロックする可能性があります。 これらの接続を許可する方法については、ウイルス対策ソフトウェアのマニュアルを参照してください。  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>ネットワーク セキュリティ ポリシーによってリモート コンピューターと Visual Studio の間の通信がブロックされる  
 ネットワーク セキュリティを調べ、通信をブロックしていないことを確認します。 Windows ネットワーク セキュリティ ポリシーの詳細については、次を参照してください。[セキュリティ ポリシー設定](/windows/device-security/security-policy-settings/security-policy-settings)です。  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>ネットワークがビジー状態でリモート デバッグをサポートできない  
 リモート デバッグを別の時点で実行するか、ネットワークでの作業を別の時点にスケジュールし直す必要がある場合があります。  
  
## <a name="more-help"></a>その他のヘルプ  
 コマンド ライン スイッチを含む、多くのリモート デバッガーのヘルプを取得する をクリックして**ヘルプ > 使用状況**リモート デバッガー ウィンドウにします。 開くことがあるない場合に次の行をコピーして、web ページを表示できます、**ファイル エクスプ ローラー**ウィンドウです。 (交換する必要があります\<Visual Studio インストール ディレクトリ > Visual Studio のインストールの場所を使用します)。  
  
 res://*\<Visual Studio インストール ディレクトリ >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)