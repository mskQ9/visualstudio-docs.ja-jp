---
ms.topic: include
ms.openlocfilehash: 0ee0234e91cdf07c2b52c39d065d527a776dc4ce
ms.sourcegitcommit: 64bf371ffe294e9b3cf769db03cf0f5c1a9b680c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666979"
---
### <a name="create-a-project-using-django-20"></a>Django 2.0 を使用してプロジェクトを作成する

現時点では、空の Django Web プロジェクト テンプレートは、最新の Django 1.x バージョンを使用します。 Django 2.x を使用する最も簡単な方法は、Django 2.x ファイルを Django 1.x プロジェクトにインストールすることです。 このプロセスに沿うことで、Visual Studio プロジェクト テンプレートで扱っている他の詳細機能を利用できます。

1. 前にセクションで説明したように、"空の Django Web プロジェクト" テンプレートを使用して Django 1.x プロジェクトを作成します。 ただし、"This project requires external dependencies"\(このプロジェクトには外部の依存関係が必要です\) というプロンプトで、**[I will install them myself]\(自分でインストールします\)** を選択してください。 このオプションを選択すると、以降の手順でアンインストールする依存関係がインストールされません。

1. コマンド プロンプトを開いて、一時フォルダーに移動します。

1. `pip install django` を実行して、グローバルな Python 環境にある最新の Django パッケージをインストールします。

1. `django-admin startproject <project_name>` を実行します。`<project_name>` は、"HelloDjango" など手順 1 で使用したものと同じプロジェクト名に置き換えてください。 `startproject` コマンドによって、ファイル `__init__.py`、`settings.py`、`urls.py`、および `wsgi.py` を格納する `<project_name>` と一致するフォルダーに加えて、`manage.py` ファイルが作成されます。

1. Visual Studio で、次のようにプロジェクト内の Django 1.x ファイルを Django 2.x ファイルに置き換えます。

  a.  **ソリューション エクスプローラー**で、`manage.py` および Django アプリ フォルダーを削除します。
  b.  プロジェクトを右クリックし、**[追加] > [既存の項目...]** コマンドを選択し、手順 4 で作成した `manage.py` ファイルに移動して選択し、**[OK]** をクリックします。 Visual Studio で、このファイルがプロジェクトにコピーされます。
  c. もう一度プロジェクトを右クリックし、**[追加] > [既存の項目...]** コマンドを選択し、手順 4 で作成したアプリ フォルダーに移動して選択し、**[OK]** をクリックします。 Visual Studio で、このフォルダー全体とその中の 4 つのファイルがプロジェクトにコピーされます。
  d. `manage.py` を右クリックして、**[Set as Startup File]\(スタートアップ ファイルとして設定\)** を選択します。

  > [!Important]
  > Visual Studio プロジェクトに示されたアプリ名は、`django-admin` ユーティリティで使用された `<project_name>` と一致している必要があります。これは、ユーティリティでは、Python コード ファイル内でその名前を名前空間として使用するためです。

1. `requirements.txt` を開き、その内容を `django >=2.0, <3` に変更して、ファイルを保存します。

1. **ソリューション エクスプローラー**で **[Python 環境]** ノードを右クリックし、**[仮想環境を追加...]** を選択します。表示されたダイアログボックスで、既定値を受け入れて、**[作成]** を選択します。 管理者特権のプロンプトをすべて承諾します。