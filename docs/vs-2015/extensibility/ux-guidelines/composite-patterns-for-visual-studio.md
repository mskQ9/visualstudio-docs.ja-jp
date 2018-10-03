---
title: Visual Studio の複合パターン |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 445b4c8a54f93e9ff479b51e432ac3a6ff823c8a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533678"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio の複合パターン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio の複合パターン](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/composite-patterns-for-visual-studio)します。  
  
複合パターンでは、個別の構成での相互作用やデザインの要素を結合します。 Visual Studio での一貫性に関して最も重要な複合パターンのいくつか挙げます。  
  
-   [データの視覚化](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [オブジェクトの UI とピークします。](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [モデルの選択](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [永続化と設定の保存](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [タッチ入力](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a> データの視覚化  
  
### <a name="overview"></a>概要  
 グラフは、視覚的に集計し、意思決定を強化するためにデータを視覚化します。 多くのデータはほとんど意味が注目に値するものと、どのようなアクションが必要がありますが直面しているユーザーに役立ちます。  
  
 ユーザーは、次の条件のいずれかに該当する場合に、グラフから活用できます。  
  
-   グラフで機能するタスクの特定のユーザーを役立ちますか。  
  
-   グラフでは、潜在的な変更の結果を予測するユーザーを有効にします。  
  
-   グラフは、傾向を発見し、パターンを特定のユーザーを役立ちますか。  
  
-   グラフは、ユーザーがより優れた意思決定を許可しますか。  
  
-   グラフに役立つ可能性のあるユーザー指定のコンテキストで特定の質問に回答しますか。  
  
#### <a name="general-rules-for-charts"></a>グラフの一般的な規則  
  
-   ラベル データ明確にします。 説明なしの図とは非常に画像。  
  
-   傾斜の縦横比を回避するために 0 で軸を開始します。 行の長さとバーのサイズは、データ ポイント間のリレーションシップを理解するための重要な視覚的手掛かりです。  
  
-   インフォ グラフィックではない、グラフを作成します。 インフォ グラフィックは、データのアートの表現との主な目的は、ビジュアルのストーリーテ リングします。 グラフは、視覚に訴えるすることができます (および必要があります) が語ら自体のデータのこと。  
  
-   Skeumorphism、棒グラフの画像、コントラスト前項、およびその他のインフォ グラフィックのしあげを回避します。  
  
-   装飾的な要素として 3D 効果を使わないでください。 場合にのみ使用が情報を理解するユーザーの機能に本当に不可欠です。  
  
-   複数の 2 つの色困難この種類のグラフを読み取って正しく解釈するように、複数の直線と塗りつぶしを使用してしないでください。  
  
-   概念を理解することや、データを操作する唯一の手段として、グラフ (または任意の図) を使用することはできません。 これは、視覚障碍を持つ、ユーザーの問題を表示します。  
  
-   ページの不要なまたは装飾的な要素としては、グラフを使用しません。 つまり、値またはヘルプのすべてのユーザーの問題を解決するグラフが追加されない場合、使用しないこと。  
  
### <a name="chart-types"></a>グラフの種類  
 Visual Studio で使用されるグラフの種類には、横棒グラフ、折れ線グラフ、リング グラフまたは「ドーナツ グラフ」、タイムラインと呼ばれる、変更された円グラフのプロット (別名「グラフをクラスター」)、およびガント チャートを散布図します。 各グラフは、さまざまな種類の情報を通信するため便利です。  
  
### <a name="other-charting-considerations"></a>その他のグラフ作成に関する考慮事項  
  
#### <a name="color"></a>色  
 Visual Studio で使用するために定義されている色をグラフの特定のパレットがあります。 パレットは、色覚の主要な種類のアクセスと、非常に狭いスライスの色として使用する場合でも、色を区別することができます。 UI に、あらゆる種類のグラフまたはグラフの任意の組み合わせでこれらの色を使用できます。 多くの特定の色を必要としない場合は、7 つのすべての色を使用する必要はありません。 これらの色は、テキスト、またはこれらの色の上にグリフを配置しないように、前景要素で使用するに設計されていません。 これらの異なる色合いをハード コーディングされ、ユーザーのカスタマイズに公開する必要があります**ツール > オプション**(を参照してください[エンドユーザーの色を公開する](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers))。  
  
|見本|16 進数|RGB|  
|------------|---------|---------|  
|![見本 71B252](../../extensibility/ux-guidelines/media/0711-71b252.png "0711_71B252")|# 71B252|113,178,82|  
|![見本bf3f00](../../extensibility/ux-guidelines/media/0711-bf3f00.png "0711_BF3F00")|# BF3F00|191,63,0|  
|![見本 FCB714](../../extensibility/ux-guidelines/media/0711-fcb714.png "0711_FCB714")|# FCB714|252,183,20|  
|![見本 903F8B](../../extensibility/ux-guidelines/media/0711-903f8b.png "0711_903F8B")|# 903F8B|144,63,139|  
|![見本 117AD1](../../extensibility/ux-guidelines/media/0711-117ad1.png "0711_117AD1")|# 117AD1|17,122,209|  
|![見本 79D7F2](../../extensibility/ux-guidelines/media/0711-79d7f2.png "0711_79D7F2")|# 79D7F2|121,215,242|  
|![見本b5b5b5](../../extensibility/ux-guidelines/media/0711-b5b5b5.png "0711_B5B5B5")|# B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a> オブジェクトの UI とピークします。  
 このセクションでは、コンテキストをでは、ピーク、コードのピーク ビューとも呼ばれるオブジェクトの UI が Visual Studio に固有の型。  
  
### <a name="overview"></a>概要  
  
-   オブジェクトの UI が得られますユーザー詳細情報や対話機能の主なタスクからそれてなし。  
  
-   Visual Studio でのオブジェクトの UI の主要なパターンは「注意の時点での情報」と呼ばれます  
  
-   Visual Studio でのオブジェクトの UI はインラインまたは浮動しか、持続性または一時的な。  
  
    -   コードのピーク ビューでの Visual Studio で、オブジェクトの UI 型は、インラインと永続的なは。  
  
    -   CodeLens では、Visual Studio で、オブジェクトの UI の型が浮動小数点と一時的です  
  
 コードの一部のしくみを理解することや、検索結果の詳細については、そのコードを開発者がコンテキストを切り替えるし、その他のコンテンツまたは別に移動することがあります ウィンドウ。 ようなコンテキストの移行は、メイン ウィンドウを離れる場合、ユーザーは、元のタスクでフォーカスを失うことができますので、混乱を招くことができます。 さらに、ウィンドウの切り替えの原因とその元のコードを他の UI に隠される場合は特に困難です。 元のコンテキストの背面であることを取得します。  
  
 オブジェクトの UI が「注意の時点での情報」という名前のパターンに従います これらのメッセージ、ポップアップ ウィンドウ、およびダイアログ ボックスは、の主なタスクにフォーカスを失うことがなく、明確化や対話機能を追加する、関連する追加の情報をユーザーに提供します。 オブジェクトの UI の例には、通知領域のアイコン、スペル ミスの単語と Visual Studio 2013 で導入されたピーク ビューの下に赤い波線の上にポインターを置いたときに表示されるポップアップ ウィンドウが含まれます。  
  
### <a name="decision-points"></a>意思決定ポイント  
 Visual Studio で、注意の時点での情報のこのパターンを使用するいくつかの方法があります。 適切なメカニズムを選択して、一貫性のある予測可能な方法で実装することは、全体的なエクスペリエンスに不可欠です。 それ以外の場合、コンテンツ自体からフォーカスに支障をきたしませんを混乱を招くまたは非整合なの経験を持つユーザーに提示することがあります。  
  
#### <a name="relationships-between-master-and-detail-content"></a>マスター/詳細コンテンツ間のリレーションシップ  
 注意の時点での情報を使用してリレーションシップを表示するコンテンツとの間、ユーザーが (「マスター」コンテンツ) に焦点とその他関連するコンテンツ (「詳細」のコンテンツ)。 このパターンで詳細コンテンツが明確にコンテンツに関連する、ユーザーは連携し、マスター コンテンツの近くに表示されることができます。 補足情報やマスター コンテンツを膨大にまとめることができない情報は、ツール ウィンドウなどの別のパターンに従う必要があります。  
  
-   **常に**近接マスター コンテンツへの詳細内容を表示します。  
  
-   **常に**詳細コンテンツは、マスターのコンテンツに専念するユーザーを引き続きを設定してください。 多くの場合、これを実現する最善の方法は、可能な限りマスター コンテンツに近いとして詳細コンテンツをレンダリングします。 これは、マスターのコンテンツの横にあるポップアップ ウィンドウに詳細コンテンツをレンダリングすることによって、またはマスター コンテンツを下にある詳細コンテンツ インラインをレンダリングすることによって実行できます。  
  
-   **決して**注意をマスター コンテンツからユーザーを受け取る時点での情報を使用します。 ユーザーは、個別に詳細内容を表示する必要がある場合は、これを行うユーザーをできるようにする明示的なアクションを公開します。  
  
#### <a name="design-details"></a>デザインの詳細  
 オブジェクトの UI が最適な選択肢を確認したらは、次の 4 つの主な設計に関する考慮事項があります。  
  
1.  **永続性:** が永続的なまたは一時的なコンテンツが必要ですか?   
    ユーザーは、情報を参照するかとの対話を表示したままにしますか。 または、ユーザーが情報にすばやく概要およびその主なタスクを続行する場合は?  
  
2.  **コンテンツの種類:** は、コンテンツ、情報、アクションにつながる、またはナビゲーションでしょうか。   
    ユーザーにマスター コンテンツに関する追加情報が必要ですか。 ユーザーは、マスターのコンテンツに影響を与えるタスクを完了する必要がありますか。 または、ユーザーは別のリソースに移動する必要がありますか。  
  
3.  **インジケーターの種類:** ことをアンビエント インジケーターは合理的ですか?   
    情報は、便利な方法で集計できマスター コンテンツを過負荷なしで表示されますか。  
  
4.  **ジェスチャ:** を呼び出すし、UI を閉じるに使用するジェスチャ何でしょうか。   
    方法はユーザー詳細コンテンツを表示し、すぐ送信でしょうか。 ピン留めすると、一時的および永続的な状態を切り替えるとなどのジェスチャを追加する値はありますか。  
  
 各これら 4 つの意思決定ポイントは、オブジェクトの UI の主要コンポーネントで影響を与えます。  
  
### <a name="on-object-ui-components"></a>オブジェクトの UI コンポーネント  
  
1.  コンテナー (コンテンツ プレゼンター) の種類  
  
    -   フローティング  
  
    -   インライン  
  
2.  コンテンツの種類  
  
    -   静的または動的になる可能性がある情報: データ  
  
    -   マスターの内容を変更するアクションにつながる: コマンド  
  
    -   別のウィンドウまたは MSDN などのアプリケーションにユーザーを移動するナビゲーション: リンク  
  
3.  ジェスチャ  
  
    -   呼び出し  
  
    -   棄却  
  
    -   ピン留め  
  
    -   他の操作  
  
4.  永続化とコミットのモデル  
  
    -   一時的  
  
    -   Durable  
  
    -   自動  
  
    -   オンデマンドで  
  
5.  アンビエント インジケーター (省略可能)  
  
    -   波線の下線  
  
    -   スマート タグ アイコン  
  
    -   他のアンビエント インジケーター  
  
#### <a name="container-content-presenter-type"></a>コンテナー (コンテンツ プレゼンター) の種類  
 注意の時点でコンテンツを利用可能な 2 つの主要なオプションがあります。  
  
1.  **インライン:** Visual Studio 2013 のコード エディターで導入された、ピーク ビューなどのインライン発表者は、既存のコンテンツの移行により、新しいコンテンツ領域。  
  
    -   **必要に応じて**使用権をプレゼントのかなりの時間を参照するか、コンテンツを操作する場合は予想される場合、インライン プレゼンターを提示します。  
  
    -   **回避**インライン発表者のユーザーが予想される場合は、概要情報を表示した後、最小限の中断で主なタスクを続行します。  
  
2.  **フローティング:** 浮動発表者が選択されたコンテンツをできるだけ近くに配置されているが、既存のコンテンツのレイアウトは変更されません。 経由でコンテンツのフローティング パネルの表示などのさまざまな方法を利用できる、選択したシンボルに空白文字が使用可能な最も近い。  
  
    -   **必要に応じて**概要情報を表示した後、最小限の中断で主なタスクを続行する必要があるユーザーの予定がある場合は、発表者を浮動小数点します。  
  
    -   **回避**をかなりを参照するか、コンテンツを操作する時間をかけたくはユーザーが予想される場合は、発表者を浮動表示します。  
  
#### <a name="content-type"></a>コンテンツの種類  
 3 つの主な種類の任意のオブジェクトの UI コンテナー内で表示できるコンテンツがあります。 これらの種類の情報の任意の組み合わせを表示できます。 次の 3 つの種類があります。  
  
1.  **情報:** ほとんどオブジェクトの UI コンテナーはある種の情報コンテンツを表示します。 コンテンツは、環境の現在の状態に関する情報を表すことができます、または環境内の潜在的な将来の状態に関する情報を表す可能性があります。 たとえば、既存のコードで、リファクタリングなどの特定のコマンドの結果を表示する使用可能性があります。  
  
    -   **常に**を表示する情報の正規表現を使用します。 たとえば、コードは、構文の強調表示、完全なコードのようになり、任意のフォントやその他の環境設定をユーザーが設定を尊重する必要があります。  
  
    -   **常に**マスター コンテンツとしてその同じ情報が表示される場合に可能になる情報のコンテンツに対するすべてのアクションのサポートを検討します。 場合は、オブジェクトの UI コンテナー内の既存のコードを表示するには、厳密にたとえばを参照し、そのコードを変更する機能をサポートします。  
  
    -   **常に**情報コンテンツを表示する潜在的な将来の状態を表している場合、別の背景色の使用を検討します。  
  
2.  アクションにつながる: 一部のオブジェクトの UI コンテナー機能が提供されるリファクタリング操作を実行するなど、マスター コンテンツに対する何らかのアクションを実行します。  
  
    -   **常に**情報コンテンツから個別に実行可能なコマンドを配置します。  
  
    -   **常に**を有効にして、該当する場合にアクションを無効にします。  
  
    -   **常に** ダイアログ ボックス内のコマンドを表すための標準的なガイドラインを参照してください。  
  
    -   **常に**オブジェクトの UI コンテナーの絶対パスで公開されているアクションの数を最小にしてください。 オブジェクトの UI と対話する軽量で高速なの経験があります。 ユーザーのオブジェクトの UI コンテナー自体を管理する方法のエネルギーを費やす必要はありません。  
  
    -   **常に**オブジェクト上の UI コンテナーが終了または破棄する方法とタイミングを検討してください。 ベスト プラクティスとして、マスター/詳細のコンテンツとの間、ダイアログの最後にある任意のアクションも閉じてくださいオブジェクトの UI コンテナーそのアクションが呼び出されたときに。  
  
3.  **ナビゲーション:** 一部オブジェクトの UI コンテナーが別のウィンドウまたは MSDN の記事をユーザーの web ブラウザーで開くなどのアプリケーションにユーザーを移動するリンクが含まれます。  
  
    -   **常に**ユーザーは、予期しないその他のコンテンツを移動できるように、[開く] のナビゲーション リンクを付加します。  
  
    -   **常に**ナビゲーション リンクをアクションにつながるリンクから分離します。  
  
#### <a name="ambient-indicators-optional"></a>アンビエント インジケーター (省略可能)  
 アンビエント インジケーターは、コードの残りの部分からコントラストの色で表示されるテキストを含む、微妙なまたは tickler シンボル波線の下線、スマート タグ アイコンなどを含め、明らかに指定できます。 アンビエント インジケーターでは、追加の関連する情報の可用性と通信します。 理想的には、有用な情報と対話するように求めるしなくても提供します。  
  
-   **常に**注意をそらすしたりユーザーを圧倒しないように、アンビエント インジケーターを配置します。 このような方法で、アンビエント インジケーターを配置することはできない場合、は、別のソリューションを検討してください。  
  
-   **常に**アンビエント インジケーターに関連するコンテンツをできるだけ近くに配置します。  
  
-   **常に**利用情報をまとめたインジケーターを作成しようとしています。 その他のデータを集計する方法と考えるか (たとえば、"3 個の参照"単に「参照」ではなく) 使用できるデータ項目の数のカウントを提供することを検討します。  
  
    -   位置インジケーターのデータことはできません常に計算され、表示の場合、すぐに、値が計算される、プログレッシブのフィードバックを提供することを検討します。 たとえば、未読の電子メールの数として Windows Phone で電子メールのライブ タイルを更新するように使用可能なデータへの更新を反映する変更をアニメーション化を検討してください。  
  
-   **決して**ユーザーが特定のコンテンツを実行できる程度よりも複数のインジケーターを追加します。 アンビエントのインジケーターは、ユーザーの介入を必要とせずに便利ですにする必要があります。 インジケーターでは、オーバーフローおよびその他の管理の制御に表示する必要がある場合、そのアンビエントが失われます。  
  
#### <a name="gestures"></a>ジェスチャ  
 マスター コンテンツにフォーカスを維持するためにユーザーを許可する際の重要な側面を開き、追加の詳細内容を消去する適切なジェスチャをサポートすることです。  
  
-   **常に**追加コンテンツを開くことによって明示的なジェスチャを実行するユーザーが必要です。 一般的なオープンのジェスチャは次のとおりです。  
  
    -   **ホバー時:** ツールヒントまたは非対話型の情報コンテンツ  
  
    -   **明示的なコマンド:** インライン プレゼンター  
  
    -   **アンビエントのインジケーターをダブルクリックします**CodeLens ポップアップ ウィンドウ。  
  
-   **常に**ユーザーが Esc キーを押すと、詳細コンテンツを消去します。  
  
-   **常に**コンテキスト オブジェクトの UI を検討します。 コンテナー内で操作できるようにするコンテンツの発表者の慎重に検討するユーザーのワークフローに悪影響を与える可能性があるポインターを合わせると、追加情報を表示するかどうか。  
  
-   **決して**を編集可能に表示されるか、ユーザーの操作への招待をポイントしたときにコンテンツを表示します。 この動作は、ツールヒントの標準の動作では、カーソルがなくなったときに、マスター経由でそれを生成したコンテンツをすぐに消去すると、詳細コンテンツ上にカーソルを移動すると、ユーザーをもたらしてことができます。  
  
##  <a name="BKMK_SelectionModels"></a> モデルの選択  
  
### <a name="overview"></a>概要  
 選択モデルを示し、ユーザー インターフェイス内で目的の 1 つまたは複数のオブジェクトに対して操作を確認するためのメカニズムです。 このトピックでは、Visual Studio のドキュメント エディター内で選択対話パターンを説明します。 テキスト エディター、デザイン画面、およびモデリング サーフェス。  
  
 ユーザーの作業では、Visual studio を示す方法が必要し、Visual Studio のフィードバックについて、運用上のユーザーにする必要があります予測どおり応答します。 相違点またはユーザーとユーザー インターフェイスの間のコミュニケーション不足は気付かないアクションを持つことができるユーザーで発生する予期しない結果。 多くの場合、エラーに気付かれないまで、ユーザーには、何かが存在しないか、変更されたことが表示されます。 選択範囲のモデルはそのため、ユーザー インターフェイスのデザインの最も重要な情報の 1 つ。 Visual Studio でモデルの選択は Windows で一貫性のあるが、若干のバリエーションがあります。  
  
 Windows のように、Visual Studio でモデルの選択は、相互作用が行われるコンテキストによって異なります。 選択内容は、4 種類のオブジェクトで発生します。  
  
-   テキスト  
  
-   グラフィカル オブジェクト  
  
-   リストとツリー  
  
-   グリッド  
  
 これらのオブジェクト内では、選択内容の 3 つの種類があります。  
  
-   連続します。  
  
-   非結合します。  
  
-   地域  
  
#### <a name="scope"></a>スコープ  
 選択範囲の最も重要なコンポーネントがどのウィンドウで作業している (activation) と、フォーカスが配置されている (選択) をある場所に、ユーザーが知っていることをすることです。 Visual Studio、Windows のウィンドウ管理機能を拡張するが、ライセンス認証スキームが同じ: ウィンドウにフォーカスを移動ウィンドウと対話します。 Visual Studio が 2 つのインジケーターのアクティブ化: ツール ウィンドウのいずれかと、ドキュメント ウィンドウのいずれか。  
  
 ドキュメントのウィンドウの前面に送信されると、その背景色を変更するは、ドキュメント ウィンドウのタブで、アクティブなウィンドウが示されます。  
  
 ![Visual Studio でのアクティブなタブ選択](../../extensibility/ux-guidelines/media/0713-01-activetab.png "0713 01_ActiveTab")  
  
 **アクティブなタブの選択**  
  
 ツール ウィンドウの場合は、アクティブなウィンドウは、ツール ウィンドウのタイトル バー領域の色の変更によって示されます。  
  
 ![Visual Studio でのアクティブなツール ウィンドウの選択](../../extensibility/ux-guidelines/media/0713-02-activetoolwindow.png "0713 02_ActiveToolWindow")  
  
 **ノードのプライマリ選択項目を示すアクティブなツール ウィンドウ**  
  
 ![Visual Studio での非アクティブなツール ウィンドウの選択](../../extensibility/ux-guidelines/media/0713-03-inactivetoolwindow.png "0713 03_InactiveToolWindow")  
  
 **ノードの潜在的な選択範囲を示す、非アクティブなツール ウィンドウ**  
  
 ウィンドウがアクティブと、そのフォーカスはガイドラインのこのセクションで説明されている選択モデルに従って示されます。  
  
#### <a name="context"></a>コンテキスト  
 Visual Studio は、ユーザーが作業しているの追跡するコンテキストの強力な概念を保持する設計されています。 1 つだけがアクティブなツールまたはドキュメント ウィンドウがあるかどうか。 ただし、最上位のドキュメント ウィンドウには常に、潜在的な選択が保持されます。 ツール ウィンドウにフォーカスがありますが、以前にアクティブだったドキュメント ウィンドウは非アクティブな状態であっても、選択を表示します。 これは、ユーザーのコンテキストを返すことができ、ツール ウィンドウおよびドキュメント ウィンドウの間でシームレスに移動できるように Visual Studio がその状態を保持していることを示す、編集、ドキュメントを保持します。  
  
### <a name="text-selection"></a>テキストの選択  
 など、組み込みのテキスト エディターのテキストに厳密には visual Studio のエディターを使用して、同じテキスト選択範囲のモデルとで外観の説明、[マウスやポインター](https://msdn.microsoft.com/library/dn742466.aspx)で Windows ユーザー エクスペリエンスの相互作用のガイドラインのページMSDN です。 テキスト エディターに入力フォーカスが挿入ポイントと呼ばれる垂直のバーによって示されます。 カーソルは、シックと逆の背後に表示されているものとして色付きの 1 つのピクセルです。 レートの設定点滅させます、**カーソルの点滅速度**での設定、**速度**のタブ、**キーボード**コントロール パネル アプレットです。  
  
#### <a name="contiguous-and-disjoint-selection"></a>連続して、不整合の選択  
 テキスト エディター内の選択範囲は、連続するのみです。 非結合テキスト選択は許可されていませんが、オブジェクトのグラフィカル エディターで対処する必要があります。 ユーザーがマウスのポインターは、テキスト領域には、カーソルは i ビームに変更します。 1 回のクリックでは、クリックした位置でテキスト エディターでカーソルを配置します。 マウス ボタンを押し、選択の強調表示を開始し、選択の強調表示を終了マウス ボタンを解放します。  
  
#### <a name="region-selection-box-selection"></a>地域の選択 (ボックスの選択)  
 Visual Studio は、テキスト エディターでリージョンの選択をサポートし、これは、ボックスの選択と呼ばれます。 ボックスの選択は、通常のテキスト ストリームに従っていないテキストの特定の領域を選択できます。 標準のテキストを選択したように選択範囲が連続している必要があります。 ボックスの選択は、Alt キーを押したままマウスでドラッグすることによって開始されます。 ボックスの選択は、alt キーと Shift キーを押しながら方向キーを使用して、選択範囲の領域も開始できます。 ボックスの選択は、通常の選択範囲の強調表示を使用し、挿入ポイント カーソル選択領域の最後に点滅していることを示します。  
  
 ![地域&#40;ボックス&#41;Visual Studio での選択](../../extensibility/ux-guidelines/media/0713-04-boxselection.png "0713 04_BoxSelection")  
  
 **Visual Studio での領域 (ボックス) の選択**  
  
#### <a name="text-selection-appearance"></a>テキスト選択範囲の外観  
 エディターでのアクティブおよび非アクティブな選択に使用する色をカスタマイズできます。 エディターの外観をカスタマイズするには、ユーザーに移動できます**ツール > オプション**、下を確認および**環境 > フォントおよび色 > テキスト エディター**します。  
  
### <a name="graphical-selection"></a>グラフィックの選択  
  
#### <a name="interaction"></a>相互作用  
 グラフィカル オブジェクトの選択は、複雑になることし、さまざまな要因によって異なります。  
  
-   **エディターのプライマリ選択項目のモデル。** グラフィカル オブジェクトを含むエディターがテキストまたはグリッドを編集することもできます。 たとえば、エディターでは、テキスト ベースのエディターなど、Visual Studio XAML デザイナーのグラフィカル オブジェクトの配置をサポートする可能性があります。 複数のオブジェクトの種類をサポートするには、ユーザーがさまざまな種類のオブジェクトから成るグループを選択する方法に影響します。  
  
-   **プライマリとセカンダリの選択状態をサポートします。** エディターでは、状態、一斉にオブジェクトを編集できるように、配置、相互の連携をサイズ変更、プライマリとセカンダリの選択を指定できます。  
  
-   **一括編集のサポート。** エディターは、編集する、グラフィカル オブジェクトの内容もできます。 たとえば、四角形には、ユーザーによって変更可能な内側のテキストも含まれます。 さらに、そのテキストを中央に配置または両端揃えで配置する可能性があります。 インプレース編集して、ユーザー操作のより詳細なレベルでは、ために、ユーザー状態情報を提示の視覚的な手掛かりの適切なセットが必要です。  
  
#### <a name="mouse-interaction"></a>マウスとの対話  
  
|入力|結果|  
|-----------|------------|  
|選択されていないオブジェクトをクリックします。|オブジェクトを選択し、オブジェクトがサイズ変更可能な場合は、破線と選択のハンドルを表示します。|  
|選択したオブジェクトをクリックします。|インプレース オブジェクトがサポートされている場合の編集をアクティブにします。 オブジェクトの外側をクリックすると、一括編集モードが無効になります。|  
|オブジェクトをダブルクリックします。|編集に関しては、オブジェクトの背後にあるコードを開き、該当する場合、既定のイベント ハンドラーを挿入する可能性があります。|  
|オブジェクトを指すため|マウス ポインターを移動カーソルに変更します。 その明るさや色などのオブジェクトの外観を変更する可能性があります。|  
|ハンドルをポイントします。|サイズ変更カーソルにポインターを変更します。 、回転をサポートするオブジェクトの選択ハンドルをいくつかは選択ハンドルに対して異なる方法で (たとえば、離れた場所に移動)、ポインターが配置されていると、回転カーソルにポインターを変更可能性があります。|  
|ドラッグ|オブジェクトが既に選択されていない場合でも、ポインターを移動カーソルに変更し、オブジェクトを移動します。|  
|エディターがフォーカスを失った|コンテンツと外観の最後の操作の選択/状態中にあるオブジェクトが保持されますが、インプレース編集モードを無効になります。|  
|オブジェクトの選択|枠線、点線、またはオブジェクトの境界を強調表示する視覚的に異なるその他の処理によって示されます。|  
|選択したオブジェクトのサイズ変更します。|ハンドルによって示されます。<br /><br /> サイズ変更可能なオブジェクトには、サイズがそれぞれの方向を表す、8 つのハンドルがあります。 場合は、オブジェクトは、特定の方向にのみ変更できより少ないハンドルを使用できます。 ユーザーには、8 つのハンドルが対話していないがあるまでオブジェクトがサイズ、ときに、4 つのハンドルを使用できます。 ハンドルのサイズとウィンドウ枠線とエッジのメトリックに結び付ける必要があります、 **GetSystemMetrics** API 関数は、ディスプレイの解像度に比例してサイズをします。<br /><br /> ![サイズ変更ハンドルを](../../extensibility/ux-guidelines/media/0713-05-resizehandles.png "0713 05_ResizeHandles")|  
|選択したオブジェクトを回転させる|![回転ハンドル](../../extensibility/ux-guidelines/media/0713-06-rotate.png "0713 06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>キーボードの相互作用  
  
|入力|結果|  
|-----------|------------|  
|タブ|エディターでオブジェクトの論理的な順序間でフォーカス インジケーターを移動します。 これは、左から右またはに応じて上下する**TabIndex** (または同等の) プロパティの値、オブジェクトの作成の順序およびエディターの全体的な目的です。 Shift キーを押しながら Tab キーでは、フォーカス インジケーターの方向を反転します。|  
|Space キー|キーストロークを保持したまま、パン モードをアクティブにします。 ビューポートの位置をパンするその他のマウス入力が必要です。|  
|Ctrl + Space|キーストロークを保持したまま、ズーム モードをアクティブにします。 ズームの倍率で増減させるのには、その他のマウス入力が必要です。|  
|Ctrl + Alt + マイナス記号|ズームの倍率を 1 つのレベルが低下します。|  
|Ctrl + Alt + プラス記号|ズームの倍率を 1 つのレベルが向上します。|  
|Shift キーまたは ctrl キー|選択範囲のグループにオブジェクトを追加します。 Ctrl キーを押しでは、オブジェクトを個別に選択範囲のグループから削除することもできます。|  
|Enter|オブジェクトの既定のコマンドを実行します (通常は開くまたは編集)。|  
|F2|オブジェクトのインプレース編集をアクティブにします。|  
|方向キー|選択したオブジェクトを少しずつ (一度に 1 ピクセルなど) での押されたキーの方向に移動します。|  
|Ctrl + 方向キー|選択したオブジェクトより大きなインクリメント (たとえば、一度に 10 ピクセル) での押されたキーの方向に移動します。|  
|Shift + 方向キー|それぞれの方向、少しずつ (一度に 1 ピクセルなど) で選択したオブジェクトのサイズを変更します。|  
|Ctrl + Shift + 方向キー|大きい単位 (たとえば、一度に 10 ピクセル) で、それぞれの方向に選択したオブジェクトのサイズを変更します。|  
  
 ユーザーは、所定の制御を編集するときにユーザー入力を自動的にサイズを変更するオブジェクトの有意義なことです。 など、ユーザーは、ラベル コントロールを編集する場合は、ラベルが、ユーザーが入力したテキストの表示に大きく必要があります。 これが行われていない場合、ユーザーする必要がありますコントロールをサイズ変更、手動でテキストを編集した後。 ユーザーがコントロールの多くの場合、rote と非生産的タスクになります。  
  
#### <a name="graphical-containers"></a>グラフィカルなコンテナー  
 場合によっては、グラフィカル エディターのコンテナーは、Windows フォーム Panel コントロールまたは HTML デザイナーで、グリッド レイアウト コントロールなどの他のグラフィカル オブジェクトを提供します。 エディターでは、その他のグラフィカル オブジェクトのコンテナーを提供する場合、コンテナーのみ (上記で説明した標準的なモデルとしてコンテナーに従ってください内のオブジェクト) の次の選択のモデルを使用する必要があります。  
  
|入力|結果|  
|-----------|------------|  
|コンテナーでのシングル クリック|直接含まれているオブジェクトのいずれかを選択することがなく、コンテナー オブジェクトを選択します。 コンテナーは移動または標準マウス/キーボード入力 (前述のように) とサイズを変更することがあります。 含まれているオブジェクトは、リレーションシップで、コンテナーに移動されますが、含まれているオブジェクトは直接も選択されている場合を除き、サイズ変更されません。|  
|コンテナーの境界領域を合わせる|コンテナーを移動できることを示すカーソルにマウスをオンにします。|  
|コンテナーの境界領域をドラッグします。|マウスを移動カーソルに変更し、コンテナー (およびに含まれているオブジェクト) に移動します。 最初にコンテナーを移動することはできません、1 回のクリックで選択されています。|  
|シングル クリックで、コンテナー内のオブジェクト|(選択) 場合、コンテナーの選択を解除し、クリックしたオブジェクトのみを選択します。|  
|Shift + または ctrl キーを押した + に含まれるオブジェクトやコンテナーをクリックします|既存の選択または選択範囲のグループに、クリックしたオブジェクトを追加します。 クリックされたオブジェクトが既に選択グループのメンバーである場合は、選択範囲のグループから削除されます。|  
  
 含まれているオブジェクトは、前のセクションで説明した基本的な選択モデルに従う必要があります。 Windows フォーム デザイナーの使いやすさのテスト、ユーザーには、(コンテナー オブジェクトによって課される) 中間の手順なしに格納されるオブジェクトはシームレスにアクセスが必要です。  
  
#### <a name="disjoint-and-region-selections"></a>非結合とリージョンの選択  
 オブジェクトのグラフィカル エディターでは、非結合選択をサポートする必要があります。 次の図に Visual Studio のコントロールの外観が表示されないことに注意してください。 参照してください[グラフィカル オブジェクトの選択範囲の外観](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance)visual 仕様の詳細についてはします。  
  
 ![非結合セレクターと領域セレクター](../../extensibility/ux-guidelines/media/0713-07-disjointregionselectors.png "0713 07_DisjointRegionSelectors")  
  
 **不整合のある選択**  
  
 グラフィカル エディターでは、選択範囲の種類の選択インジケーターでリージョンの選択内容も提供します。 グラフィカル エディターでは、その他のオブジェクトの種類 (テキスト) などをサポートする場合、リージョンの選択できない可能性がありますに応じてその他のオブジェクトの種類の制約。  
  
 ![選択範囲](../../extensibility/ux-guidelines/media/0713-08-marqueeselection.png "0713 08_MarqueeSelection")  
  
 **マーキーの選択**  
  
#### <a name="primary-and-secondary-selections"></a>プライマリとセカンダリの選択  
 グラフィカル オブジェクトの一部のエディターでは、グループ内のオブジェクトを編集またはユーザーを許可します。 この場合、プライマリとセカンダリの選択項目の概念を導入する必要があります。 プライマリの選択は、オブジェクトには、その他のすべてのオブジェクトがグループ操作の応答です。 ユーザーが最初に選択したオブジェクトがプライマリのコントロールになり、以降の選択が、セカンダリの選択になります。 プライマリの選択には、セカンダリのものを選択するオブジェクトがプライマリであることを示すから個別の視覚的処理があります。  
  
 ![プライマリとセカンダリ選択](../../extensibility/ux-guidelines/media/0713-09-primarysecondary.png "0713 09_PrimarySecondary")  
  
 **プライマリの選択の 2 つのセカンダリ選択**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> グラフィカル オブジェクトの選択範囲の外観  
 ハンドルは、オブジェクトの境界ボックスの周囲の四角形パターンで描画される四角形です。 次の表では、グラフィカル オブジェクトを含めることができるハンドル、サイズ変更、および一括編集の外観をさまざまな状態の例を示します。 ハンドルのサイズをウィンドウの境界線とメトリックを使用してエッジに関連付けられる必要があります、 **GetSystemMetrics** API。  
  
|状態|外観|ビジュアルの詳細|  
|-----------|----------------|--------------------|  
|**選択されていません。**|既定値|![既定のボタンの状態](../../extensibility/ux-guidelines/media/0713-10-defaultstate.png "0713 10_DefaultState")||  
|**プライマリ選択**|サイズ変更可能です|![サイズ変更ハンドルを使ったプライマリ選択](../../extensibility/ux-guidelines/media/0713-11-primaryresize.png "0713 11_PrimaryResize")|![サイズ変更ハンドルを使ったプライマリ選択&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-12-primaryresizezoom.png "0713 12_PrimaryResizeZoom")|  
|**プライマリ選択**|サイズを変更しません。|![プライマリ選択せずにサイズ変更ハンドル](../../extensibility/ux-guidelines/media/0713-13-primarynoresize.png "0713 13_PrimaryNoResize")|![プライマリ選択せずにサイズ変更ハンドル&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-14-primarynoresizezoom.png "0713 14_PrimaryNoResizeZoom")|  
|**プライマリ選択**|ロックされています|![ロックされたプライマリ選択](../../extensibility/ux-guidelines/media/0713-15-primarylocked.png "0713 15_PrimaryLocked")|![ロックされたプライマリ選択&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-16-primarylockedzoom.png "0713 16_PrimaryLockedZoom")|  
|**セカンダリ選択**|サイズ変更可能です|![サイズ変更ハンドルを使ったセカンダリ選択](../../extensibility/ux-guidelines/media/0713-17-secondaryresize.png "0713 17_SecondaryResize")|![サイズ変更ハンドルを使ったセカンダリ選択&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-18-secondaryresizezoom.png "0713 18_SecondaryResizeZoom")|  
|**セカンダリ選択**|サイズを変更しません。|![セカンダリ選択せずにサイズ変更ハンドル](../../extensibility/ux-guidelines/media/0713-19-secondarynoresize.png "0713 19_SecondaryNoResize")|![サイズ変更なしのセカンダリ選択&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-20-secondarynoresizezoom.png "0713 20_SecondaryNoResizeZoom")|  
|**セカンダリ選択**|ロックされています|![ロックされたセカンダリ選択](../../extensibility/ux-guidelines/media/0713-21-secondarylocked.png "0713 21_SecondaryLocked")|![ロックされたセカンダリ選択&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-22-secondarylockedzoom.png "0713 22_SecondaryLockedZoom")|  
|**アクティブな UI**|既定値|![UI のアクティブな状態](../../extensibility/ux-guidelines/media/0713-23-uiactive.png "0713 23_UIActive")|![UI のアクティブな状態&#40;拡大&#41;](../../extensibility/ux-guidelines/media/0713-24-uiactivezoom.png "0713 24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>選択範囲のモデルの表示  
  
#### <a name="tree-view"></a>ツリー ビュー  
 ツリー ビューでの選択には、単純な強調表示が表示されます。 ユーザーは、ノード名またはノードのアイコンをクリックすると、ノードが選択されます。 ノードの左側にある三角形のグリフを展開またはコントラクトのツリー コントロールが、例外が 1 つのユーザーの選択には影響しません。 そのノードの子ノードを選択しているときは、親ノードを折りたたみ、時に選択を親に移動します。  
  
 ![Visual Studio での一般的なツリー ビュー](../../extensibility/ux-guidelines/media/0713-25-treeview.png "0713 25_TreeView")  
  
 **Visual Studio での一般的なツリー ビュー**  
  
 ツリー ビューでは、ツリー内の複数のレベルでも、連続して、不整合の選択をサポートできます。 連続または不整合のある複数の選択肢が表示されているツリー ノードで行う必要があります。 ノードが折りたたまれている場合は、不整合のある選択が失われ、ノードが折りたたまれている、選択範囲を取得します。 これにより、ユーザー操作によって影響を受けるノードが表示されます。 ノードが折りたたまれている場合になります不明なノードの影響を受ける可能性があります。  
  
 親ノードが選択されている場合は、親とそのすべての子に適用する操作の適切な場所の場合もありますが、操作が、親を適用してください。 この場合、チェック ボックスまたはユーザーに、"すべての子に適用する オプションを明示する確認のダイアログ ボックスなど、操作中に追加の UI を提供します。  
  
##### <a name="renaming"></a>名前の変更  
 ツリー内のノードが名前の変更をサポートしている場合に名前の変更を行ってください。 一括操作では、Visual Studio でのすべてのツリー コントロール全体で標準的な必要があります。 変更、テキストを選択した場合、ユーザー入力を受け入れる準備ができてのノードの名前全体をカバーする、インプレース編集モードでは、すぐにアクティブにするコマンドを提供します。 ノードは、ファイルを表している場合、ファイル名は、拡張機能を含める必要があります。 選択範囲の表示には、ファイル名と拡張子ではなくの本文のみを含める必要があります。  
  
|入力|結果|  
|-----------|------------|  
|Enter キー|名前の変更操作をコミットします。|  
|Esc キー|名前の変更操作をキャンセルします。|  
|一括編集領域の外側をクリックして|名前の変更操作をコミットします。|  
|元に戻す|名前の変更操作をキャンセルする簡単に元に戻すを提供します。|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>リストとグリッド コントロール内の選択  
 リストの選択における主要な概念とは、行ベースでは、選択範囲には、行全体が行われることを意味が単位として選択されているです。 これに対し、グリッドには、行の他の側面に影響を与えずに選択する特定のセルを許可できます。 グリッドは、入れ子になった行の (、TreeGrid など) を選択し、親の行とやり取りして選択解除すると、階層の分岐全体を許可する階層を含めることも可能性があります。 選択リストでは、行全体のデータの単純な強調表示色で表示されます。 フォーカスは、現在の編集可能な行またはセル (行のすべてのセルは読み取り専用の場合) を囲む 1 ピクセルの点線で表示されます。  
  
> [!NOTE]
>  **フォーカス**と**選択**は異なる概念です。 *フォーカス*UI の要素が対象となることを示しています中に別のオブジェクトに明示的に向けられた入力を受信する*選択*の後続の対象のオブジェクトのセット内のオブジェクトの包含状態を参照操作は、場所にかかる場合があります。  
  
 連続した、不整合のある、リストの選択項目がありますまたは地域。 複数の選択が許可されている、連続してサポート領域 (ボックス) の選択は、非結合選択をサポート常にする必要がありますは省略可能です。 リージョンの選択は、リストの本文の空白にドラッグすることによって開始されます。  
  
|Object|選択ツール|  
|------------|---------------|  
|リスト|連続します。|常にサポートされます (複数選択を許可する) 場合。|  
|リスト|非結合します。|常にサポートされます (複数選択を許可する) 場合。|  
|リスト|地域|省略可能なサポート。 リストの本文の空白文字で、マウスをドラッグして開始します。|  
  
 リストに対する 1 回クリックすると、クリックが発生した行を選択します。 ユーザーの動作のインプレース編集をサポートする一覧のセルをクリックして、一括編集用セルもすぐにアクティブになります。 それ以外の場合、行全体では、すぐに選択され、強調表示を示しています。  
  
 リストの本文でドラッグすることは次の 3 つのいずれかを行います。  
  
-   リストをサポートしていると、マウス ダウンは、空白である場合は、地域の選択を開始します。  
  
-   一覧のセルまたは行は、ドラッグ ソースをサポートしている場合は、ドラッグ アンド ドロップ操作を開始します  
  
-   現在の行を選択します。  
  
##### <a name="in-place-editing"></a>埋め込み先編集  
 インプレース編集が許可されている場合は、2 つの基本的なモデルがあります。 単純な編集コントロールとプロパティを選択します。 単純な編集コントロールでは、コンテンツは、強調表示されているし、ユーザー入力のインプレース編集がアクティブになるとすぐに準備が整います。 プロパティの一覧が実装されている場合、インプレース編集モードがアクティブになるし、現在の選択項目が強調表示されていないプロパティ ピッカーを起動するボタンが表示されます。 選択 でなければなりません右揃え、セル。 一括編集の例については、次を参照してください。、**プロパティ ウィンドウ**と**タスク一覧**Visual Studio でします。  
  
##### <a name="keyboard-support"></a>キーボードのサポート  
 キーボードのサポートの選択リストとグリッドでは、Windows の標準の規則に従います。  
  
-   方向キーは、フォーカスを移動すると、行またはセルを選択すると、一覧を移動します。  
  
-   Shift + 方向キー、矢印の方向に、隣接した選択を実行します。  
  
-   Ctrl + space キーの切り替えを追加して、不整合のある選択範囲を作成、選択範囲からリスト項目を削除するの後に矢印。  
  
-   グリッドの入れ子になった階層が含まれている場合、右矢印キーの親の行では、展開および左矢印キーを折りたたみ 1 つ。  
  
-   Tab キーでは、セルが編集可能な場合に、現在の行にセル間でフォーカスを移動します。  
  
-   Enter キーの項目一覧で、既定のコマンドを実行します (多くの場合、**オープン**)。  
  
-   F2 キーは、現在選択されているセルのインプレース編集をアクティブにします。  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a> 永続化と設定の保存  
  
### <a name="overview"></a>概要  
 Visual Studio 内の各ソフトウェア コンポーネントですが、独自の状態と永続化を担当は、通常、Visual Studio に自動的によっては、設定などと共に保存ウィンドウ サイズと位置。 次の表は、自動的に保存された設定と明示的なユーザーまたはプログラム実行するアクションをな設定の組み合わせです。  
  
|Object|内容を保存するには|保存する場合|保存する場所|  
|------------|------------------|------------------|-------------------|  
|選択可能なオブジェクト (たとえば、コードの行の場合)|コード行のブレークポイント<br /><br /> コードの行に関連付けられているユーザーのショートカット|プロジェクトが保存されます。|**ユーザー オプション (.suo)** プロジェクトのファイル|  
|ダイアログ|移動された場合、ダイアログの場所<br /><br /> ダイアログ ボックスで、ユーザーが最後に使用するビュー|ダイアログ ボックスを閉じたとき<br /><br /> Visual Studio セッションが終了します。|メモリ内<br /><br /> レジストリに**HKEY_Current_User**|  
|[Window]|ウィンドウの位置とサイズ|ウィンドウを閉じたとき<br /><br /> Visual Studio のモードが変更されたとき<br /><br /> Visual Studio セッションが終了します。|**ユーザー オプション (.suo)** プロジェクトのファイル<br /><br /> ウィンドウの設定のカスタム オプション ファイル|  
|ドキュメント|ドキュメントの現在の選択<br /><br /> ドキュメントのビュー<br /><br /> ユーザーがアクセスした最後の複数の場所|ドキュメントが保存されます。|**ユーザー オプション (.suo)** プロジェクトのファイル|  
|プロジェクト|ファイルへの参照<br /><br /> ディスク上のディレクトリへの参照<br /><br /> その他のソフトウェアへの参照<br /><br /> コンポーネント<br /><br /> プロジェクト自体に関する状態情報|プロジェクトが保存されます。|プロジェクト ファイル|  
|ソリューション|プロジェクトへの参照<br /><br /> ファイルへの参照|プロジェクトまたはソリューションを保存すると|**ソリューション (.sln)** ファイル|  
|設定**ツール > オプション**|キーボードのカスタマイズ<br /><br /> ツールバーのカスタマイズ<br /><br /> 色スキーム|ときに、**ツール > オプション**ダイアログ ボックスを閉じる<br /><br /> Visual Studio セッションが終了します。|レジストリに**HKEY_Current_User**|  
  
 ユーザーによるを行っていると、実行、場合によって決まります (セッション間ではレジストリ設定として)、ディスクに保存 (セッション)、中にメモリ内で、設定を保存するかどうかファイルの一部として、プロジェクトまたはソリューション自体の一部としての**ソリューションオプション (.suo)** ファイル、またはカスタム設定がそのソフトウェアのコンポーネントだけをファイルとして認識します。 上記の表には、設定の保存されたいくつかのイベントが表示されます。 ただし、状態を保存する場合があります。  
  
-   ユーザーがダイアログ ボックスまたはウィンドウ内の場所を変更する場合  
  
-   ユーザーが別のウィンドウにフォーカスを転送する場合  
  
-   設計をデバッグ モードに切り替えたとき  
  
-   ユーザーが自分のアカウントをログオフすると  
  
-   コンピューターが休止状態に移行またはシャット ダウン  
  
-   コンピューター/ハード ドライブの場合は、再フォーマットされ、再度セットアップするには  
  
### <a name="window-configurations"></a>ウィンドウの構成  
 ウィンドウの構成は、開発環境の基本的なプレゼンテーション – 存在するツール ウィンドウの一覧と配置される方法で構成されるスキームです。 IDE (IDE windows) によって管理される、windows の Visual Studio を終了すると、最後のときに、IDE のウィンドウ レイアウトを表示と同じユーザーが起動するため、ユーザーごとのレイアウト情報が永続化されます。 状態と IDE ウィンドウの位置は、XML 形式のカスタム オプションをファイルに保存されます。 IDE に読み込まれるパッケージによって作成されるツール ウィンドウは、レジストリでは状態情報を保持し、可能性がありますや、ユーザーごとにできない可能性があります。  
  
#### <a name="profile-specific-layouts"></a>プロファイルに固有のレイアウト  
 各プロファイルに固有の開発者のペルソナを使い慣れた方法で編成、ツール ウィンドウのレイアウトが含まれています (Visual C 開発者に表示される、**ソリューション エクスプ ローラー** をc#開発者が期待できるときに、IDEの左側にあります。**ソリューション エクスプ ローラー**右側)。 プロファイルに固有のウィンドウ レイアウトは、ユーザーが起動時にプロファイルを選択した後に読み込まれます。 パッケージの作成者は、把握、ユーザーがウィンドウの構成に加える変更は保持し、顧客のエクスペリエンスでは、最も適したウィンドウ レイアウトを決定する必要があります。  
  
##  <a name="BKMK_TouchInput"></a> タッチ入力  
 ユーザーは、タッチ デバイスで、マイクロソフト開発製品をますます増えています。 ただし、タッチ デバイスでの開発ツールを使用するが難しく障壁があります。 ユーザーには、信頼性が高く、正確なタッチ エクスペリエンスを提供する製品が期待されます。 これらのガイドラインの目的は、タッチ機能を組み込むし、Visual Studio および関連製品の間で一貫性のあるタッチ エクスペリエンスをお勧めしますに関する意思決定を通知するためにです。  
  
### <a name="levels-of-experience"></a>経験のレベル  
 次のレベルのエクスペリエンスではチームの決定に役立つガイドを提供するタッチで投資関心のある目的のレベルに応じてタッチ機能を提供するがします。  
  
-   **基本的な経験**作業全体で終端がないために、チームを提供するタッチ機能はします。  
  
-   **エクスペリエンスを最適化**(たとえば、通常の利用可能なインターネット ブラウザー アプリケーションで) 機能の最も一般的なタッチを提供するチームにとっては。  
  
-   **エクスペリエンスの上位権限による**はジェスチャとしてこのような機能を追加するチームまたは他のオプションの機能、アプリケーションを構成することができます - タッチ フレンドリーします。  
  
||基本的な経験|最適化されたエクスペリエンス|管理者特権でのエクスペリエンス|  
|-|----------------------|--------------------------|-------------------------|  
|ユーザーをできるようにしています.|コードとソリューション/プロジェクトのレベル終端なしの読み取りを修正します。|保守、リファクタリング、およびナビゲーションのタスクを実行します。|信頼度で一貫性のある、直感的な滑らかなエクスペリエンスで動作します。|  
|エディター|タッチ パンと選択<br /><br /> スクロール バーのタッチ ジャンプし押しながらドラッグするには|ピンチ ズーム<br /><br /> 高速スクロール<br /><br /> 選択ツール<br /><br /> コンテキスト メニューの使いやすい||  
|最上位のツール ウィンドウ|一覧のパン<br /><br /> 項目の選択<br /><br /> スクロール バーのタッチ ジャンプし押しながらドラッグするには|簡単な項目スクロールと選択||  
|ウィンドウ化||ウィンドウのサイズ変更します。<br /><br /> クイック アクセス||  
|ドキュメント ウェル||開いているファイルの間に簡単に移動||  
|ジェスチャ||一般的なジェスチャは、IDE 全体で作業を確認します。|ジェスチャ ベースのアクション<br /><br /> ドラッグ アンド ドロップし、デザイナーをサポートします。|  
|その他の注意事項|||カスタムのオンスクリーン キーボード|  
  
#### <a name="gestures"></a>ジェスチャ  
 ジェスチャは、それ以外の場合より複雑な対話を必要とするコマンドのショートカットをユーザーに提供します。 Windows のガイドラインを参照[デスクトップ アプリケーションの一般的なタッチ ジェスチャ](http://msdn.microsoft.com/library/windows/desktop/dd940543\(v=vs.85\).aspx)、パンとズームなどの単純なジェスチャを含め、ほとんどのジェスチャには、このガイダンスに従います。
