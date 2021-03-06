---
title: 変更ログ (Visual Studio Tools for Unity、Mac) | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d43542dc78c8bc0eaeb05e1a620edff7a88efa37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31084120"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>変更ログ (Visual Studio Tools for Unity、Mac)
Visual Studio Tools for Unity の変更ログです。

## <a name="1501"></a>1.5.0.1
 リリース: 2018 年 3 月 28 日
 
### <a name="new-features"></a>新機能

-   **統合:**

    -   Unity プロジェクト エクスプローラーが追加テンプレート対応になりました。

## <a name="1500"></a>1.5.0.0
 リリース: 2018 年 3 月 21 日
 
### <a name="new-features"></a>新機能

-   **統合:**

    -   USB 経由で Android プレーヤーを検出し、接続できるようになりました。

## <a name="1403"></a>1.4.0.3
 リリース: 2018 年 3 月 5 日
 
### <a name="new-features"></a>新機能

-   **プロジェクトの生成:**

    -   Unity 2018.1 の新しいプロジェクト ジェネレーターのサポートが追加されました。

-   **統合:**

    -   専用設定のオプション パネルが追加されました。

## <a name="1402"></a>1.4.0.2
 リリース: 2018 年 1 月 24 日
 
### <a name="bug-fixes"></a>バグ修正

-   **プロジェクトの生成:**

    -   Mono バージョンの検出を修正しました。

-   **統合:**

    -   2018.1 とプラグインのアクティブ化のタイミングの問題を修正しました。

    -   新しいプレーヤーを検出したときの通知を修正しました。

## <a name="1401"></a>1.4.0.1
 リリース: 2018 年 1 月 23 日
 
### <a name="bug-fixes"></a>バグ修正

-   **統合:**

    -   ダブルクリックによるフォルダーの展開/折りたたみを修正しました。

## <a name="1400"></a>1.4.0.0
 リリース: 2017 年 12 月 13 日
 
### <a name="new-features"></a>新機能

-   **プロジェクトの生成:**

    -   .NET Standard のサポートを追加しました。

### <a name="bug-fixes"></a>バグ修正

-   **統合:**

    -   pdb から mdb への自動デバッグ シンボル変換を修正済み

## <a name="1301"></a>1.3.0.1
 リリース: 2017 年 12 月 12 日
 
### <a name="bug-fixes"></a>バグ修正

-   **統合:**

    -   配列のサイズを変更するときに、インスペクターに影響する EditorPrefs.GetBool への間接的な呼び出しを修正しました。

-   **ウィザード:**

    -   roslyn コンテキストは、メソッドの挿入前に更新されます。

## <a name="1300"></a>1.3.0.0
 リリース: 2017 年 11 月 20 日
 
### <a name="new-features"></a>新機能

-   **ウィザード:**

    -   "Unity メッセージの実装" ウィザードを追加しました。

    -   VS for Mac 7.4 で新しい入力候補 API のサポートが追加されました。

## <a name="1200"></a>1.2.0.0
 リリース: 2017 年 10 月 23 日
 
### <a name="new-features"></a>新機能

-   **デバッガー:**

    -   ポータブル デバッグ シンボル ファイルのサポートが追加されました。

### <a name="bug-fixes"></a>バグ修正

-   **プロジェクトの生成:**

    -   アセンブリのファイル名に余分な .dll 拡張子が誤って追加される問題を修正しました。

    -   既定値が 'true' になったので、AllowAttachedDebuggingOfEditor Unity フラグを強要しません。

## <a name="1103"></a>1.1.0.3
 リリース: 2017 年 10 月 23 日
 
### <a name="new-features"></a>新機能

-   **プロジェクトの生成:**

    -   .NET 4.6 プロファイルのサポートが追加されました。

## <a name="1102"></a>1.1.0.2
 リリース: 2017 年 8 月 8 日
 
### <a name="new-features"></a>新機能

-   **デバッガー:**

    -   アタッチする Unity がわからない場合、[プロセスにアタッチ] ダイアログを開始します。

-   **プロジェクトの生成:**

    -   Unity 5.6 の使用時にはアンセーフ コンパイル スイッチが常に有効になります。

## <a name="1101"></a>1.1.0.1
 リリース: 2017 年 7 月 20 日
 
### <a name="new-features"></a>新機能

-   **統合:**

    -   ローカライズされたリソースのサポートが追加されました。

## <a name="1100"></a>1.1.0.0
 リリース: 2017 年 7 月 12 日
 
### <a name="new-features"></a>新機能

-   **統合:**

    -   [プロセスにアタッチ] ウィンドウからプレーヤーやエディターにアタッチできるようになりました。

-   **プロジェクトの生成:**

    -   mcs.rsp ファイルを使用したアセンブリ名の参照が修正されました。

    -   assembly.json コンパイル単位のサポートが追加されました。    

    -   API レベルの定義が修正されました。    

### <a name="bug-fixes"></a>バグ修正

-   **統合:**

    -   コンパイル時のシェーダー エラー メッセージを修正しました。

## <a name="1001"></a>1.0.0.1
 リリース: 2017 年 5 月 4 日
 
### <a name="bug-fixes"></a>バグ修正

-   **統合:**

    -   ハイブリッド プロジェクトと標準プロジェクトのアクティブ ドキュメント追跡を修正しました。

## <a name="1000"></a>1.0.0.0
 リリース: 2017 年 5 月 3 日
