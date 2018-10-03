---
title: ドメイン固有言語について |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 971c63d25aee9c8676921b5ee7e112ae41a8a251
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544392"
---
# <a name="about-domain-specific-languages"></a>ドメイン固有言語について
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ドメイン固有言語について](https://docs.microsoft.com/visualstudio/modeling/about-domain-specific-languages)します。  
  
C# または UML などの汎用言語とは異なり、ドメイン固有言語 (DSL) は、特定の問題の領域またはドメイン内のステートメントを表現する設計されています。  
  
 既知の Dsl には、正規表現と SQL が含まれます。 各 DSL は、独自のスコープ外にある考え方を説明するテキスト文字列またはデータベースがより上の操作を記述するため、汎用言語よりも好転します。 個々 の業界では、独自の Dsl もあります。 たとえば、電気通信業界で呼び出す説明の言語を使用する電話の呼び出しでの状態のシーケンスと無線で旅行業界は広く DSL は、フライトの予約の記述に使用される標準。  
  
 ビジネスとプロジェクトは、DSL で記述される可能性がありますの概念の特別なセットを扱うもします。 たとえば、これらのアプリケーションのいずれかの DSL を定義できます。  
  
-   Web サイトでのナビゲーション パスのプランです。  
  
-   電子部品の配線図。  
  
-   コンベヤ ベルトの荷物取り扱い設備空港用ネットワーク。  
  
 定義する DSL を設計するとき、*ドメイン クラス*各 Web ページ、lamp、または空港では、チェックイン デスクなど、ドメインで重要な概念。 定義する*ドメイン リレーションシップ*ハイパーリンク、線、または概念を相互にリンクするコンベヤ ベルトなど。  
  
 DSL のユーザー作成*モデル。* モデルは*インスタンス*DSL の。 たとえば、特定の Web サイト、または特定のデバイス、または処理システムで特定の空港の手荷物受取所の配線がについて説明します。  
  
 ユーザーは、ダイアグラム、または Windows フォームとしてモデルを表示できます。 モデルも表示できます XML として格納されている方法であります。 DSL を定義するときにユーザーの画面上の各ドメイン クラスとリレーションシップのインスタンスの表示方法を定義します。 一般的な DSL は、一連のアイコンと矢印で接続されている四角形として表示されます。  
  
 次の図では、図表の DSL で小さなモデルを示しています。  
  
 ![Tudor ファミリ ツリー モデル](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Dsl で行うことができます。  
 DSL の一般的なアプリケーションでは、プログラム コードまたは他の成果物を生成します。 DSL を定義するときに定義できます*テキスト テンプレート*する DSL のモデルを読み取るし、テキスト ファイルを生成します。  
  
 たとえば、空港、プランを受け取り、荷物取り扱い、および一部のユーザー ドキュメント、プランを記述するために、ソフトウェアの一部を生成するテンプレートを記述できます。  
  
 DSL を定義した場合は、自分のコンピューターにインストールする他のユーザーに配布できます。 DSL のユーザーを作成し、でモデルを編集[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
 メニュー コマンドを定義することもでき、ユーザーに役立つその他のツールは、DSL に役立ち、DSL が適切に使用できるユーザー項目テンプレートが新しいインスタンスを作成する検証制約を編集します。 ツールとその他の 1 つまたは複数の Dsl をラップする[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能として統合パッケージです。  
  
 通常、開発チームがあるいくつかの製品のようなコードを記述する際に、ドメイン固有言語が作成されます。 たとえば、荷物取り扱いシステムを専門とする会社から生成できるため、いくつかのインストールごとに、コードの荷物追跡 DSL を定義できます。 DSL の利点は、することによって認識できる、お客様から生成されたコードが信頼性が高く、こと、およびことシステム迅速に更新できる、お客様の要件を変更する場合です。  
  
 [!INCLUDE[dsl](../includes/dsl-md.md)] 独自のグラフィカルなデザイナーと、独自のダイアグラムの表記のあるドメイン固有言語を作成し、各プロジェクトの適切なソース コードを生成する言語を使用できます。  
  
## <a name="domain-specific-development"></a>ドメイン固有の開発  
 ドメイン固有の開発は、ドメイン固有言語を使用して、言語を構築し、アプリケーション開発者へのデプロイによってモデル化できるアプリケーションの部分を識別するプロセスです。 開発者がアプリケーションに固有のモデルを構築、モデルを使用して、ソース コードを生成して、アプリケーションを開発するソース コードを使用するドメイン固有言語を使用します。  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>ドメイン固有のグラフィカルな開発の側面  
 グラフィカルなドメイン固有言語には、次の機能を含める必要があります。  
  
-   Notation  
  
-   ドメイン モデル  
  
-   成果物の生成  
  
-   シリアル化  
  
-   Visual Studio との統合  
  
### <a name="notation"></a>Notation  
 ドメイン固有言語を簡単に定義されているし、ドメイン固有の構造を表す拡張が可能な要素の適切な小ささのセットが必要です。 表記法では、図形は、要素を表し、およびダイアグラムをグラフィカルに画面上の要素間のリレーションシップを表す、コネクタで構成されます。 [!INCLUDE[dsl](../includes/dsl-md.md)]図形を拡張し、洗練されている、ドメイン固有言語の要素を表します。  
  
### <a name="domain-model"></a>ドメイン モデル  
 ドメイン固有言語には、要素と一貫した文法にそれらの関係のセットを組み合わせる必要があります。 要素および関係の組み合わせが有効かどうかも定義があります。 たとえば、プログラミング言語には、循環継承、1 つのクラスは、2 番目のクラスから派生し、2 番目のクラスが最初のクラスから派生した通常ようにします。 制約を使用してビジネス ロジックを表現することもできます、たとえば、1 人のユーザーが自身の依存をすることはできません。 [!INCLUDE[dsl](../includes/dsl-md.md)] ほとんどのドメイン固有言語を必要とする制限の種類を表現するのにには、制約を使用します。  
  
### <a name="artifact-generation"></a>成果物の生成  
 ドメイン固有言語の主な目的の 1 つは、ソース コード、XML ファイル、またはその他のいくつかの使用可能なデータなどの成果物を生成します。 通常、モデルでの変更は、成果物の変更を意味します。 使用することができます[!INCLUDE[dsl](../includes/dsl-md.md)]成果物を生成して、モデルを変更するときに、その再生成します。  
  
### <a name="serialization"></a>シリアル化  
 ドメイン固有言語は、編集、保存でき、閉じている、再読み込みするなんらかの形で永続化する必要があります。 [!INCLUDE[dsl](../includes/dsl-md.md)] XML 形式の定義し、ドメイン固有言語をシリアル化または永続化する方法をカスタマイズすることができますを使用します。  
  
### <a name="integration-with-visual-studio"></a>Visual Studio との統合  
 [!INCLUDE[dsl](../includes/dsl-md.md)]でホストされている[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、拡張多く[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ウィンドウとコントロール。 メニュー コマンド、ツールボックス項目、およびユーザー インターフェイスの他の要素の動作をカスタマイズすることもできます。  
  
 ドメイン固有言語、モデル バス アダプターを作成することもできます。 このアダプターには、モデルの参照と、モデルとコードを記述することがアクセスでき、DSL のインスタンスを更新できます内の要素ができます。 強力なモデル バス メカニズムを使用して記述できます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]複数のモデルを使用する拡張機能。 モデルを使用するスタンドアロン アプリケーションを記述することもできます。 詳細については、次を参照してください。 [Visual Studio modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)します。  
  
## <a name="benefits-of-domain-specific-development"></a>ドメイン固有の開発の利点  
 ドメイン固有言語には、次の利点があります。  
  
-   問題の領域を正確に適合する構成要素が含まれています。  
  
     汎用の言語とは異なり、ドメイン固有言語は、要素と、問題領域のロジックを直接表す関係ので構成されます。 たとえば、保険アプリケーションには、ポリシーと要求の要素を含める必要があります。 ドメイン固有言語では、アプリケーション、および検索とロジックのエラーの修正を設計するやすくなります。  
  
-   開発者以外と全体的な設計を理解するドメインを知らない人のことができます。  
  
     グラフィカルなドメイン固有言語を使用すると、開発者以外が、アプリケーションの設計を簡単に理解できるように、ドメインの視覚的表現を作成できます。  
  
-   最終的なアプリケーションのプロトタイプを作成しやすくなります。  
  
     開発者は、クライアントに表示できる、プロトタイプ アプリケーションを作成する、モデルを生成するコードを使用できます。  
  
## <a name="the-process-of-domain-specific-development"></a>ドメイン固有の開発のプロセス  
 ドメイン固有言語を使用するほとんどのソフトウェア開発チームでは、作成し、そのモデルを使用して、次の手順に従います。  
  
-   チームは、決して変更しない部分からドメインの変数部分を識別します。  
  
-   開発者は、固定の部品用のコードを記述し、変数の部品用の拡張ポイントのままにします。  
  
-   リード ソフトウェア開発者やアーキテクトは、ドメインおよび可変部分の拡張機能ポイントの固定部分の設計パターンが組み込まれているドメイン固有言語を作成します。  
  
-   リード ソフトウェア開発者やアーキテクトは、ドメイン固有言語、チームが生成するさまざまなアプリケーションの開発者にデプロイされます。  
  
-   すべての開発者は、特定のアプリケーションに適用されるモデルを作成します。


