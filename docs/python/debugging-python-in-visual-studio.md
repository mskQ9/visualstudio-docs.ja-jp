---
title: Python コードのデバッグ
description: ブレークポイントの設定、ステップ実行、値の検査、例外の確認、対話型ウィンドウでのデバッグなど、特に Python コードについての Visual Studio でのデバッグ機能のチュートリアルです。
ms.date: 07/13/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 14716aa85245dcbd7c1ba0bc85824f5a53bece2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079824"
---
# <a name="debug-your-python-code"></a>Python コードのデバッグ

Visual Studio は、実行中のプロセスへのアタッチ、ウォッチ ウィンドウやイミディエイト ウィンドウでの式の評価、ローカル変数の調査、ブレークポイントの設定、ステートメントのステップ イン/ステップ アウト/ステップ オーバー、次のステートメントの設定など、Python 向けの総合的なデバッグ機能を提供します。

シナリオ固有のデバッグに関する次の記事も参照してください。

- [Linux リモート デバッグ](debugging-python-code-on-remote-linux-machines.md)
- [Azure リモート デバッグ](debugging-remote-python-code-on-azure.md)
- [Python/C++ 混合モード デバッグ](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [混合モード デバッグのシンボル](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | Python デバッグのデモについては、[こちらのビデオ (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) をご覧ください (3 分 32 秒)。|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Visual Studio の Python は、プロジェクトを使用しないデバッグをサポートしています。 スタンドアロンの Python ファイルを開き、エディター内で右クリックして、**[デバッグの開始]** を選択すると、Visual Studio がグローバルな既定の環境 (「[Python Environments](managing-python-environments-in-visual-studio.md)」 (Python 環境) を参照) を使用して、引数なしでスクリプトを起動します。 ただし、それ以降は、フル機能のデバッグ サポートが提供されます。
>
> 環境と引数を制御するには、コードのプロジェクトを作成します。プロジェクトは、[[既存の Python コードから]](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) プロジェクト テンプレートを使用して簡単に作成できます。

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>デバッグの基本

デバッグの基本的なワークフローには、ブレークポイントの設定、コードのステップ実行、値の検査、例外の処理が含まれます。これらについては、後続のセクションで説明します。

デバッグ セッションを開始するには、**[デバッグ] > [デバッグの開始]** コマンド、ツールバーの **[開始]** ボタン、または F5 キーを使用します。 これらの操作で、プロジェクトのアクティブな環境と、プロジェクトのプロパティで指定されているコマンドライン引数や検索パスを使用して、プロジェクトのスタートアップ ファイル (ソリューション エクスプローラーで太字で表示) が起動します (「[プロジェクトのデバッグ オプション](#project-debugging-options)」を参照してください)。 **Visual Studio 2017 バージョン 15.6** 以降では、スタートアップ ファイルが設定されていない場合は警告が表示されます。それより前のバージョンでは、Python インタープリターが実行された出力ウィンドウが開くか、表示されても短時間で消えていきます。 どの場合も、適切なファイルを右クリックし、**[スタートアップ ファイルとして設定]** を選びます。

> [!Note]
> デバッガーは常に、プロジェクトのアクティブな Python 環境で起動します。 環境を変更するには、[プロジェクト用の Python 環境の選択](selecting-a-python-environment-for-a-project.md)に関する記事の説明に従って、別の環境をアクティブにします。

### <a name="breakpoints"></a>ブレークポイント

ブレークポイントを設定すると、マークしたポイントでコードの実行が停止するので、プログラムの状態を確認することができます。 ブレークポイントを設定するには、コード エディターの左端の余白をクリックするか、コード行を右クリックして **[ブレークポイント] > [ブレークポイントの挿入]** を選択します。 ブレークポイントが設定された行には赤い点が表示されます。

![Visual Studio でのブレークポイント](media/debugging-breakpoints.png)

赤い点をクリックするか、コード行を右クリックして **[ブレークポイント] > [ブレークポイントの削除]** を選択すると、ブレークポイントが削除されます。 **[ブレークポイント] > [ブレークポイントの無効化]** コマンドを使用して、ブレークポイントを削除せずに無効にすることもできます。

> [!Note]
> 他のプログラミング言語を使用してきた開発者の場合、Python の一部のブレークポイントに驚く可能性があります。 Python では、ファイル全体が実行可能コードであるため、最上位のクラスまたは関数定義を処理するためにファイルが読み込まれたときに、そのファイルが実行されます。 ブレークポイントが設定されていると、クラス宣言の途中でデバッガーが中断されることがあります。 驚くかもしれませんが、これは正常な動作です。

ブレークポイントをトリガーする条件は、カスタマイズすることができます。たとえば、変数が特定の値または値の範囲に設定されたときにのみ中断するなどです。 条件を設定するには、ブレークポイントの赤い点を右クリックして **[条件]** を選択し、Python コードを使用して式を作成します。 Visual Studio のこの機能の詳細については、「[Breakpoint conditions (ブレークポイント条件)](../debugger/using-breakpoints.md#breakpoint-conditions)」を参照してください。

条件を設定するときに、**[アクション]** も設定することができます。出力ウィンドウに表示するメッセージを作成し、必要に応じて自動で実行を継続できます。 メッセージをログに記録すると、ログ コードを直接アプリケーションに導入しなくても、*トレースポイント*が作成されます。

![ブレークポイントでのトレースポイントの作成](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>コードのステップ実行

ブレークポイントで停止したら、次に再び停止するまで、コードをさまざまな方法でステップ実行したり、コードのブロックを実行したりできます。 これらのコマンドは、上部の [デバッグ] ツールバー、**[デバッグ]** メニュー、コード エディターの右クリック コンテキスト メニュー、ショートカット キーなど、さまざまな場所から利用できます (すべての場所ですべてのコマンドを利用できるわけではありません)。

| 機能 | キー操作 | 説明 |
| --- | --- | --- |
| [続行] | F5 | 次のブレークポイントに到達するまでコードを実行します。 |
| [ステップ イン] | F11 | 次のステートメントを実行して停止します。 次のステートメントが関数の呼び出しの場合、呼び出されている関数の最初の行でデバッガーが停止します。 |
| [ステップ オーバー] | F10 | 次のステートメントを関数の呼び出しを含めて実行 (すべてのコードを実行) し、戻り値をすべて適用します。 ステップ オーバーでは、デバッグする必要のない関数を簡単にスキップすることができます。 |
| [ステップ アウト] | Shift + F11 | 現在の関数の終わりまでコードを実行し、呼び出し元のステートメントに戻ります。  このコマンドは、現在の関数の残りの部分をデバッグする必要がない場合に便利です。 |
| [カーソル行の前まで実行] | Ctrl + F10 | エディターのキャレット位置までコードを実行します。 このコマンドを使用すると、デバッグする必要がないコードのセグメントを簡単にスキップすることができます。 |
| 次のステートメントの設定 | Ctrl + Shift + F10 | コードの現在の実行ポイントを、キャレットの位置に変更します。 このコマンドを使用すると、エラーがある場合や望ましくない副作用があることがわかっている場合などに、コードのセグメントが実行されないようスキップすることができます。 |
| 次のステートメントの表示 | Alt + Num * | 次に実行されるステートメントに戻ります。 このコマンドは、コード内のさまざまな場所をチェックしたために、デバッガーがどこで停止しているかわからなくなってしまった場合に便利です。 |

### <a name="inspecting-and-modifying-values"></a>値の検査と変更

デバッガーで停止中に、変数の値を検査して変更することができます。 ウォッチ ウィンドウを使用して、個々の変数やカスタム式を監視することもできます (詳しくは[変数の検査](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows)に関する記事を参照してください)。

データヒントを使用して値を表示するには、エディター内で変数の上にマウスを合わせます。 値をクリックして変更することができます。

![デバッガーのデータヒント](media/debugging-quick-tips.png)

自動変数ウィンドウ (**[デバッグ] > [ウィンドウ] > [自動変数]**) には、現在のステートメントに近い変数と式が表示されます。 値を編集するには、値列をダブルクリックするか、値列を選択して F2 キーを押します。

![デバッガーの自動変数ウィンドウ](media/debugging-autos-window.png)

ローカル ウィンドウ (**[デバッグ] > [ウィンドウ] > [ローカル]**) には、現在のスコープ内のすべての変数が表示されます。この値も編集できます。

![デバッガーのローカル ウィンドウ](media/debugging-locals-window.png)

自動変数ウィンドウとローカル ウィンドウの使用方法について詳しくは、「[Inspecting Variables in the Autos and Locals Windows (自動変数ウィンドウおよびローカル ウィンドウでの変数の検査)](../debugger/autos-and-locals-windows.md)」を参照してください。

ウォッチ ウィンドウ (**[デバッグ] > [ウィンドウ] > [ウォッチ 1 ～ 4]** ) では、任意の Python 式を入力して結果を表示できます。 式は、ステップごとに再評価されます。

![デバッガーのウォッチ ウィンドウ](media/debugging-watch-window.png)

ウォッチ ウィンドウの使用方法について詳しくは、「[Setting a Watch on Variables using the Watch and QuickWatch Windows (ウォッチ ウィンドウとクイック ウォッチ ウィンドウを使用して変数のウォッチ ポイントを設定する)](../debugger/watch-and-quickwatch-windows.md)」を参照してください。

文字列値 (ここでは、`str`、`unicode`、`bytes` および `bytearray` はすべて文字列と見なします) を検査する際、値の右側に虫眼鏡のアイコンが表示されます。 このアイコンをクリックすると、ポップアップ ダイアログに引用符なしの文字列値が表示されます。テキストは改行およびスクロールされるので、長い文字列の場合に便利です。 さらに、このアイコンのドロップダウン矢印を選択すると、プレーン テキスト、HTML、XML、または JSON のビジュアライザーを選択できます。

![文字列のビジュアライザー](media/debugging-string-visualizers.png)

HTML、XML、JSON のビジュアライザーは別のポップアップ ウィンドウに表示されます。構文が強調表示され、ツリー ビューで表示されます。

### <a name="exceptions"></a>例外

プログラムのデバッグ中にエラーが発生し、そのエラーの例外ハンドラーがない場合、デバッガーは例外の発生ポイントで中断します。

![例外のポップアップ](media/debugging-exception-popup.png)

ここで、呼び出し履歴を含めたプログラムの状態を検査することができます。 ただし、コードのステップ実行を試みると、例外は、処理されるかプログラムが終了するまでスローされ続けます。

**[デバッグ] > [ウィンドウ] > [例外設定]** メニュー コマンドを選択すると、ウィンドウが開き、**[Python Exceptions (Python 例外)]** を展開することができます。

![例外ウィンドウ](media/debugging-exception-settings.png)

各例外のチェックボックスは、その例外が発生したときに "*常に*" デバッガーを中断するかどうかを制御します。 特定の例外で中断する頻度を増やすには、該当するチェックボックスをオンにします。

既定では、ほとんどの例外は、ソース コードに例外ハンドラーが見つからないときに中断します。 この動作を変更するには、例外を右クリックし、**[ユーザー コードで処理されない場合は続行]** オプションを変更します。 特定の例外で中断する頻度を減らすには、該当するチェックボックスをオフにします。

この一覧に表示されていない例外を構成するには、**[追加]** ボタンをクリックして追加します。 この名前は、例外の完全名と一致している必要があります。

## <a name="project-debugging-options"></a>プロジェクトのデバッグ オプション

既定では、デバッガーは標準的な Python ランチャーを使用してプログラムを起動します。コマンドライン引数も、特別なパスや条件も使用しません。 スタートアップ オプションはプロジェクトのデバッグ プロパティで変更することができます。デバッグ プロパティにアクセスするには、ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロパティ]** を選択して、**[デバッグ]** タブを選択します。

![プロジェクトのデバッグ プロパティ](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>起動モードのオプション

| オプション | 説明 |
| --- | --- |
| 標準的な Python ランチャー | CPython、IronPython、および Stackless Python などのバリエーションと互換性のあるポータブル Python で記述されたコードのデバッグに使用します。 純粋な Python コードをデバッグするのに最適です。 このランチャーは、実行中の `python.exe` プロセスにアタッチする場合に使用されます。 このランチャーには CPython 用の[混合モード デバッグ](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)も用意されており、C/C++ コードと Python コードとの間でシームレスなステップ実行ができます。 |
| Web ランチャー | 起動時に既定のブラウザーを起動し、テンプレートのデバッグを有効にします。 詳細については、[Web テンプレートのデバッグ](python-web-application-project-templates.md#debugging)に関する記事を参照してください。 |
| Django Web ランチャー | Web ランチャーと同じです。旧バージョンと互換性のために記載しています。 |
| IronPython (.NET) ランチャー | .NET デバッガーを使用します。IronPython でのみ機能しますが、C# や VB を含む任意の .NET 言語プロジェクト間でステップ実行ができます。 このランチャーは、IronPython をホストしている実行中の .NET プロセスにアタッチする場合に使用されます。 |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>実行オプション (検索パス、スタートアップ引数、環境変数)

| オプション | 説明 |
| --- | --- |
| 検索パス | これらの値は、ソリューション エクスプローラーのプロジェクトの [検索パス] ノードに表示される内容と同じです。 ここで値を変更することもできますが、ソリューション エクスプローラーを使用した方が、フォルダーを参照したり、自動で相対パスに変換したりできるので簡単です。 |
| スクリプトの引数 | これらの引数は、スクリプトを起動するコマンドのスクリプト ファイル名の後ろに追加されます。 ここで指定した引数は、スクリプトで、最初の引数は `sys.argv[1]`、2 番目の引数は `sys.argv[2]` (その後も同様) として利用できます。 |
| Interpreter Arguments (インタプリターの引数) | これらの引数は、ランチャーのコマンドラインのスクリプト名の前に追加されます。 警告をコントロールする `-W ...`、プログラムを少し最適化する `-O`、バッファーなし IO を使用する `-u` などがよく使用されます。 IronPython のユーザーは、多くの場合、このフィールドを使用して `-X` オプションを渡します (`-X:Frames` や `-X:MTA` など)。 |
| Interpreter Path (インタープリターのパス) | 現在の環境に関連付けられているパスをオーバーライドします。  非標準のインタープリターを使用してスクリプトを起動する場合に便利です。 |
| 環境変数 | 複数行のテキスト ボックスで、`NAME=VALUE` の形式でエントリを追加します。 この設定は最後に適用されます。既存のグローバル環境変数よりも優先され、検索パスの設定に従って `PYTHONPATH` が設定された後に適用されるため、これらの変数を手動でオーバーライドするために使用できます。 |

<a name="the-debug-interactive-window"></a>

## <a name="immediate-and-interactive-windows"></a>イミディエイト ウィンドウと対話型ウィンドウ

デバッグ セッション中に使用できる対話型ウィンドウは 2 つあります。標準の Visual Studio イミディエイト ウィンドウと、Python Debug Interactive ウィンドウです。

イミディエイト ウィンドウ (**[デバッグ] > [ウィンドウ] > [イミディエイト]**) は、Python 式を即座に評価したり、実行中のプログラム内の変数を検査したり割り当てたりする際に使用します。 詳細については、[イミディエイト ウィンドウ](../ide/reference/immediate-window.md)に関する一般的な記事を参照してください。

Python Debug Interactive ウィンドウ (**[デバッグ] > [ウィンドウ] > [Python Debug Interactive]**) は、より豊富な機能を備えています。コードの記述と実行を含め、[対話型 REPL](python-interactive-repl-in-visual-studio.md) のすべてのデバッグ機能を利用できます。 Python Debug Interactive ウィンドウは、標準的な Python ランチャーを使用して、デバッガー内で開始しているすべてのプロセスに自動的に接続します (**[デバッグ] > [プロセスにアタッチする]** でアタッチされたプロセスも含みます)。 ただし、C/C++ の混合モード デバッグを使用している場合、Debug Interactive ウィンドウは使用できません。

![Python Debug Interactive ウィンドウ](media/debugging-interactive.png)

Debug Interactive ウィンドウは、[標準の REPL コマンド](python-interactive-repl-in-visual-studio.md#meta-commands)に加えて、特別なメタコマンドをサポートしています。

| コマンド | 引数 | 説明 |
| --- | --- | --- |
| `$continue`、`$cont`、`$c` | 現在のステートメントからプログラムの実行を開始します。 |
| `$down`, `$d` | スタック トレースで現在のフレームを 1 つ下のレベルに移動します。 |
| `$frame` | | 現在のフレーム ID を表示します。
| `$frame` | フレーム ID | 現在のフレームを指定のフレーム ID に切り替えます。
| `$load` | ファイルからコマンドを読み込み、完了するまで実行します。 |
| `$proc` |  | 現在のプロセス ID を表示します。 |
| `$proc` | プロセス ID | 現在のプロセスを指定のプロセス ID に切り替えます。 |
| `$procs` | | 現在デバッグ中のプロセスの一覧を表示します。 |
| `$stepin`、`$step`、`$s` | 次の関数呼び出しにステップ インします (可能な場合)。 |
| `$stepout`、`$return`、`$r` | 現在の関数からステップ アウトします。 |
| `$stepover`、`$until`、`$unt` | 次の関数呼び出しにステップ オーバーします。 |
| `$thread` | | 現在のスレッド ID を表示します。 |
| `$thread` | スレッド ID | 現在のスレッドを指定のスレッド ID に切り替えます。 |
| `$threads` | | 現在デバッグ中のスレッドの一覧を表示します。 |
| `$up`, `$u` | | スタック トレースで現在のフレームを 1 つ上のレベルに移動します。 |
| `$where`、`$w`、`$bt` | 現在のスレッドのフレームを一覧表示します。 |

標準のデバッガー ウィンドウのプロセス、スレッド、呼び出し履歴などは、Debug Interactive ウィンドウとは同期されないことに注意してください。 Debug Interactive ウィンドウでアクティブなプロセス、スレッド、またはフレームを変更しても、他のデバッガー ウィンドウに影響はありません。 同様に、他のデバッガー ウィンドウでアクティブなプロセス、スレッド、またはフレームを変更しても、Debug Interactive ウィンドウに影響はありません。

Debug Interactive ウィンドウには独自のオプションがあり、**[ツール] > [オプション] > [Python Tools] > [Debug Interactive ウィンドウ]** からアクセスできます。 Python 環境ごとに個別のインスタンスを持つ通常の Python Interactive ウィンドウとは異なり、Debug Interactive ウィンドウのインスタンスは 1 つだけで、デバッグ中のプロセスには常に Python インタープリターが使用されます。 [「Options for Python in Visual Studio」(Visual Studio の Python のオプション) の「Debugging options」(デバッグ オプション)](python-support-options-and-settings-in-visual-studio.md#debugging-options) を参照してください。

![Python Interactive ウィンドウのオプション](media/debugging-interactive-options.png)

## <a name="use-the-experimental-debugger"></a>試験的デバッガーを使用

Visual Studio 2017 Preview 4.0 以降では、ptvsd バージョン 4.1 以降をベースにした "試験的デバッガー" の使用をオプトインすることができます。 オプトインするには、**[ツール]** > **[オプション]** メニュー コマンドの順に選択し、[オプション] ダイアログ ボックス内で **[Python]** > **[試験的]** の順に移動し、**[試験的デバッガーを使用]** を選択します。

試験的デバッガーは、次の表に示すように、限られた Python 環境とのみ互換性があります。

| Python のバージョン | 試験的デバッガーとの互換性 |
| --- | --- |
| 2.6 | × |
| 2.7 | [はい] |
| 3.1 から 3.4 | × |
| 3.5 以降 | [はい] |
| IronPython | × |

互換性のない環境で試験的デバッガーの使用を試みた場合、Visual Studio には "デバッガーはこの環境と互換性がありません" というエラーが表示されます。

![試験的デバッガーの使用時に表示される、エラー "デバッガーはこの環境と互換性がありません"](media/debugging-experimental-incompatible-error.png)

**[Disable the experimental debugger]\(試験的デバッガーを無効にします\)** コマンドを選択します。これにより、**[試験的デバッガーを使用]** オプションがクリアされます。

> [!Note]
> 現時点で、Python 3.3 および 3.4 の場合、この警告は表示されません。

現在の環境で ptvsd の以前のバージョンをインストールした場合 (リモート デバッグに必要なバージョン 3.x に対して以前のバージョン 4.0.x の場合など)、Visual Studio には、"デバッガー パッケージを読み込めませんでした" というエラー、または "デバッガー パッケージが最新ではありません" という警告が表示されます。

![試験的デバッガーの使用時に表示されるエラー "デバッガー パッケージを読み込めませんでした"](media/debugging-experimental-version-error.png)

![試験的デバッガーの使用時に表示される警告 "デバッガー パッケージが最新ではありません"](media/debugging-experimental-version-warning.png)

ptvsd のインストールを管理するには、**[Python 環境]** ウィンドウの **[パッケージ]** タブを使用するか、またはコマンドラインから次のコマンドを使用します。

```ps
# Uninstalling ptvsd causes VS to default to its bundled 4.1.x version.
pip uninstall ptvsd

# Upgrading ptvsd gives you the latest version, which may be newer than the bundled version.
# -pre is required to allow pre-release versions as currently required by the experimental debugger.
pip install --upgrade ptvsd -pre
```

> [!Important]
> ptvsd の一部のバージョンについては警告を無視してもかまいませんが、Visual Studio は正しく動作しない可能性があります。

## <a name="see-also"></a>関連項目

Visual Studio のデバッガーについて詳しくは、「[Debugging in Visual Studio (Visual Studio でのデバッグ)](../debugger/debugger-feature-tour.md)」を参照してください。
