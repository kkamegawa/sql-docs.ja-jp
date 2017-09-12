---
title: "チュートリアルの学習の SQL Server マシン |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- Python
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 32
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0ebeae12d6987154baa7ccb7c9417e9f92b2bbe0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-machine-learning-tutorials"></a>SQL Server の Machine Learning のチュートリアル

この記事では、チュートリアル、デモ、および SQL Server 2016 または SQL Server 2017 において、マシン学習機能を使用するサンプル アプリケーションの包括的な一覧を提供します。 T-SQL から R、Python またはを実行、リモートとローカル コンピューティング コンテキストを使用して SQL 運用環境のため、R、Python コードを最適化する方法を学習するには、ここから開始します。

## <a name="start-here"></a>ここから開始

+ [Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)

+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)

要件と設定を取得する方法の詳細については、次を参照してください。[の前提条件](#bkmk_prerequisites)です。

## <a name="samples-and-solutions"></a>サンプルとソリューション

+ [サンプル](#bkmk_samples) 

    SQL Server 開発チームのこれらの実際のシナリオでは、機械学習をアプリケーションに埋め込む方法を示します。 すべてのサンプルでは、実稼働のダウンロード、変更、および使用するコードを含めます。

+ [ソリューション](#bkmk_solutions) 

    Microsoft データ サイエンス チームからのテンプレートはカスタマイズ可能な高速で、機械学習を開始するためです。 各ソリューションは、特定のタスクや業界の問題; に合わせてさらに、SQL server または Azure Machine Learning などのクラウド環境で実行するほとんどのソリューションが設計されています。 その他のソリューションは、Microsoft R Server または HDI Spark クラスターで実行できます。

### <a name ="bkmk_samples"></a>SQL Server 製品サンプル

これらのサンプルと SQL Server と R Server 開発チームによって提供されるデモは、実際のアプリケーションに埋め込まれた分析を使用する方法を選択します。

+ [顧客を実行する R と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  セグメントの顧客売上データに基づいて教師なし学習を使用します。 この例では、Microsoft R からの拡張性の高い rxKmeans アルゴリズムを使用して、クラスタ リング モデルを構築します。 
  
  適用されます SQL Server 2016 または SQL Server 2017。

+ [新機能！顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Kmeans アルゴリズムを使用して、顧客の監視対象外のクラスタ リングを実行する方法を説明します。 この例では、Python 言語でのデータベースを使用します。 
    
    適用されます SQL Server 2017。

+ [R と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Ski レンタル ビジネス可能性がありますの機械学習を将来のレンタルを予測するのに役立つ、今後の要求を満たすには、ビジネス プランとスタッフを使用する方法について説明します。 この例では、Microsoft R アルゴリズムを使用して、ロジスティック回帰とデシジョン ツリー モデルを構築します。 
  
  適用されます SQL Server 2016 または SQL Server 2017。

+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

   今後の必要性を計画するために、Python を使用して ski レンタル分析アプリケーションをビルドします。 この例は、新しい Python ライブラリを使用して**revoscalepy**、線形回帰モデルを作成します。 
   
   適用されます SQL Server 2017。

### <a name="bkmk_solutions"></a>ソリューション テンプレート

Microsoft データ サイエンス チームは、一般的なシナリオのソリューションをすぐに開始するために使用するソリューション テンプレートを提供しています。 トレーニングおよび SQL Server のストアド プロシージャを使用してスコア付けのモデルを配置する方法の指示を含む、すべてのコードを示します。

+ [不正行為の検出](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [顧客離れ予測](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [予測メンテナンス](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [病院状態置かれる時間を予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

詳細については、「[Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/)」 (SQL Server 2016 R Services の機械学習テンプレート) を参照してください。

## <a name="more-resources-and-reading"></a>複数のリソースと読み取り

+ [理由で作成のでした。 ですか。](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    R Services の背後にある実際の状況を確認します。 開発と、原点と SQL Server R Services の目的を説明する PM チームから、この記事を参照します。

+ [チュートリアルおよび Microsoft R のサンプル データ](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    Microsoft R とクイック チュートリアルのこのコレクションで、RevoScaleR パッケージで提供されるものについて説明します。 RevoScaleR データ ソースとリモート計算コンテキストを使用して 1 回の R コードを記述して、どこにでも展開する方法を説明します。

+ [MicrosoftML を概要します。](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

  高度なモデリングと複数のコンピューティング コンテキスト用に最適化された、スケーラブルなデータ変換の MicrosoftML パッケージで新しいアルゴリズムを使用する方法を説明します。

## <a name="bkmk_Prerequisites"></a>前提条件

これらのチュートリアルを実行するには、ダウンロードして、前述のように、コンポーネントを学習する SQL Server コンピューターをインストールする必要があります。

+ [SQL Server R Services セットアップします。](../r/set-up-sql-server-r-services-in-database.md)
+ [SQL Server の Python Services セットアップします。](../python/setup-python-machine-learning-services.md)

SQL Server 2017、R、Python またはその両方をインストールできます。 それ以外の場合、全体的なセットアップ プロセス、アーキテクチャ、および要件は、同じです。

SQL Server セットアップを実行した後、これらの重要な手順を必ず。

1. 実行して、外部スクリプト実行機能を有効にする`sp_configure 'external scripts enabled', 1`です。 再構成、SQL Server を再起動するための手順に従います。
2. SQL Server インスタンスに接続できること、ワーカー アカウントが使用して、スタート パッド サービスが実行されていることを確認してください。
3. SQL ログインと R または Python スクリプトを実行する Windows ユーザー アカウントに関連付けられているアクセス許可を確認します。 すべてには、R、または Python スクリプトを実行して、インスタンスに接続するアクセス許可が必要があります。 サンプルでは、によって、データベース オブジェクトを作成して、データを読み書きするアクセス許可を必要することもあります。

詳細については、一般的なセットアップと構成の問題は、この資料を参照してください: [Machine Learning のサービスのトラブルシューティング](../machine-learning-troubleshooting-faq.md)

> [!NOTE]
> 別のオープン ソース R または Python のツールを使用してこれらのチュートリアルを実行することはできません。 開発環境と、SQL Server コンピューターの両方と machine learning、R、または Python で提供されるライブラリ、Microsoft SQL Server とリモート計算コンテキストの使用との統合をサポートするが必要です。
