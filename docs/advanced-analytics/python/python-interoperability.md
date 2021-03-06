---
title: SQL Server の Machine Learning Python 相互運用性 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3ad52bb3774c1534ac745e1dc93d18c75260723c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202574"
---
# <a name="python-interoperability-with-sql-server"></a>SQL Server での Python の相互運用性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機能を有効にした場合にインストールされている Python コンポーネントを説明**Machine Learning Services (In-database)** 言語としての Python を選択します。

## <a name="python-components"></a>Python コンポーネント

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Python の実行可能ファイルを変更しません。 Python ランタイム SQL ツールとは別にインストールされているし、外部で実行される、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]プロセスです。

特定の関連付けられている配布[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスがインスタンスに関連付けられているフォルダーにあります。

たとえば、Python オプションの既定のインスタンスで Machine Learning のサービスがインストールされている場合は、下になります。

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

SQL Server 2017 Machine Learning Services のインストールでは、Python の Anaconda ディストリビューションを追加します。 具体的には、Anaconda 3 インストーラーは、に基づいて使用 Anaconda 4.3 分岐します。 SQL Server 2017 の想定されている Python レベルは、Python 3.5 です。

## <a name="new-python-packages-in-this-release"></a>このリリースで新しい Python パッケージ

Anaconda ディストリビューションがサポートされているパッケージの一覧は、Continuum analytics サイトを参照してください: [Anaconda パッケージの一覧](https://docs.continuum.io/anaconda/pkg-docs)

SQL Server 2017 で machine Learning サービスも含まれています、新しい**revoscalepy** Python のライブラリです。

このライブラリを提供するのと同等の機能、 **RevoScaleR**パッケージを Microsoft r です。つまり、さまざまなスケーラブルな機械学習モデルと同様に、リモート計算コンテキストの作成のサポートをなど**rxLinMod**です。 RevoScaleR に関する詳細については、次を参照してください。[分散し、並列コンピューティング ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing)です。

[For Python microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) Python をインストールに追加するときに、SQL Server の Machine Learning の一部としてパッケージがインストールされています。 このパッケージには、多くの機械学習の速度と精度、最適化されているだけでなく、行内テキストとイメージの操作に変換するアルゴリズムが含まれています。 詳細については、「 [MicrosoftML パッケージを SQL Server で使用](https://docs.microsoft.com/sql/advanced-analytics/using-the-microsoftml-package)です。

Microsoftml と revoscalepy を密に結合します。microsoftml で使用されるデータ ソースは、revoscalepy オブジェクトとして定義されます。 Revoscalepy 転送 microsoftml へのコンテキストの制限事項を計算します。 つまり、すべての機能はローカルの操作に使用できるが、RxInSqlServer リモート計算コンテキストを切り替える必要があります。

## <a name="using-python-in-sql-server"></a>SQL Server での Python の使用

インポートする、 **revoscalepy** Python コードとし、モジュールから関数を呼び出すモジュールなどの他の Python 関数。

Python の入力データを表形式にする必要があります。 形式ですべての Python の結果を返す必要がある、**パンダ**データ フレーム。

ストアド プロシージャにスクリプトを埋め込むことで、T-SQL では、内部、Python コードを実行できます。

または、ローカル Python IDE からコードを実行してリモート コンピューティング コンテキストを定義することで、SQL Server コンピューターで実行されるスクリプト。

ローカル データの操作、SQL Server または他の ODBC データ ソースからデータを取得したり XDF ファイル形式を使用して R ソリューションや他のソースでデータを交換できます。

**詳細については**

+ サポートされている関数: [revoscalepy とは](what-is-revoscalepy.md) 
+ サポートされるデータ型の Python: [Python ライブラリとデータ型](python-libraries-and-data-types.md)
+ サポートされているデータ ソース: ODBC データベース、SQL Server、および XDF ファイル
+ 計算コンテキストをサポートしますローカル、または SQL Server。

### <a name="licensing"></a>ライセンス

Python の Machine Learning のサービスのインストールの一環として、GNU Public License の条項に同意する必要があります。

## <a name="see-also"></a>参照

[Python ライブラリとデータ型](python-libraries-and-data-types.md)
