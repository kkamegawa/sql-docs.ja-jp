---
title: 統計の作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: statistics
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-statistics
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.stat.properties.f1
- sql13.swb.statistics.filter.f1
- sql13.swb.stat.columns.f1
- sql13.swb.statistics.propertis.f1
helpviewer_keywords:
- creating statistics
- statistics [SQL Server], creating
ms.assetid: 95a455fb-664d-4c95-851e-c6b62d7ebe04
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f4a06d45ab3fa089f07e31ac8b8fd9a3162e820f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32972567"
---
# <a name="create-statistics"></a>統計の作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のテーブルまたはインデックス付きビューの 1 つまたは複数の列で、クエリの最適化に関する統計 (フィルター選択された統計情報を含む) を作成できます。 ほとんどのクエリでは、高品質のクエリ プランに必要な統計がクエリ オプティマイザーによって既に生成されていますが、最適な結果を得るために追加の統計情報を作成する必要がある場合もあります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **統計を作成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   CREATE STATISTICS ステートメントで統計を作成する前に、AUTO_CREATE_STATISTICS オプションがデータベース レベルで設定されていることを確認します。 これにより、クエリ オプティマイザーが常にクエリ述語列について 1 列ずつの統計を作成し続けるようになります。  
  
-   統計オブジェクトごとに最大 32 列の一覧を取得できます。  
  
-   フィルター選択された統計情報の述語で定義されているテーブル列の定義を削除、名前変更、または変更することはできません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 ユーザーがテーブルまたはインデックス付きビューの所有者であるか、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、または **db_ddladmin** 固定データベース ロールのメンバーである必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-statistics"></a>統計を作成するには  
  
1.  **オブジェクト エクスプローラー**で、新しい統計を作成するデータベースをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[テーブル]** フォルダーを展開します。  
  
3.  プラス記号をクリックして、新しい統計を作成するテーブルを展開します。  
  
4.  **[統計]** フォルダーを右クリックし、 **[新しい統計]** をクリックします。  
  
     **[全般]** ページの *[テーブルの新しい統計 - <テーブル名>]* ダイアログ ボックスに次のプロパティが表示されます。  
  
     **テーブル名**  
     統計の対象となるテーブルの名前が表示されます。  
  
     **[統計名]**  
     統計情報が格納されるデータベース オブジェクトの名前が表示されます。  
  
     **[統計の列]**  
     このグリッドに、この統計の対象となる列が表示されます。 グリッド内のすべての値は読み取り専用です。  
  
     **名前**  
     統計の対象となる列の名前が表示されます。 表示されるのは、1 つのテーブルの 1 つの列、または列の組み合わせです。  
  
     **[データ型]**  
     統計の対象となる列のデータ型を表します。  
  
     **[サイズ]**  
     各列のデータ型のサイズが表示されます。  
  
     **Identity**  
     オンの場合、ID 列を示します。  
  
     **[NULL を許容]**  
     列で NULL 値が許容されるかどうかを示します。  
  
     **[追加]**  
     テーブルの列を統計グリッドに追加します。  
  
     **[削除]**  
     選択されている列を統計グリッドから削除します。  
  
     **[上へ移動]**  
     統計グリッド内で選択されている列を上に移動します。 グリッド内の列の位置は、統計の実用性に大きく影響します。  
  
     **[下へ移動]**  
     統計グリッド内で選択されている列を下に移動します。  
  
     **[これらの列に対する統計の最終更新日時]**  
     統計がどれだけ古いかを示します。 統計は、新しいほど価値があります。 データに大きな変更が加えられた後や、通常とは異なるデータを追加した後は、統計を更新してください。 データの変更が平均しているテーブルの場合は、統計を頻繁に更新する必要はありません。  
  
     **[この列の統計を更新する]**  
     オンにすると、ダイアログ ボックスを閉じたときに統計を更新します。  
  
     **[フィルター]** ページの *[テーブルの新しい統計 - <テーブル名>]* ダイアログ ボックスに次のプロパティが表示されます。  
  
     **[フィルター式]**  
     フィルター処理された統計情報にどのデータ行を含めるかを定義します。 たとえば、IPv4 アドレスの場合、「 `Production.ProductSubcategoryID IN ( 1,2,3 )`  
  
5.  **[全般]** ページの *[テーブルの新しい統計 - <テーブル名>]* ダイアログ ボックスで **[追加]** をクリックします。  
  
     **[列の選択]** ダイアログ ボックスに次のプロパティが表示されます。 この情報は読み取り専用です。  
  
     **名前**  
     統計の対象となる列の名前が表示されます。 表示されるのは、1 つのテーブルの 1 つの列、または列の組み合わせです。  
  
     **[データ型]**  
     統計の対象となる列のデータ型を表します。  
  
     **[サイズ]**  
     各列のデータ型のサイズが表示されます。  
  
     **Identity**  
     オンの場合、ID 列を示します。  
  
     **Allow NULLs**  
     列で NULL 値が許容されるかどうかを示します。  
  
6.  **[列の選択]** ダイアログ ボックスで、統計を作成する列のチェック ボックスをオンにし、 **[OK]** をクリックします。  
  
7.  *[テーブルの新しい統計 - <テーブル名>]* ダイアログ ボックスで、**[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-statistics"></a>統計を作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Create new statistic object called ContactMail1  
    -- on the BusinessEntityID and EmailPromotion columns in the Person.Person table.   
  
    CREATE STATISTICS ContactMail1  
        ON Person.Person (BusinessEntityID, EmailPromotion);   
    GO  
    ```  
  
4.  上記で作成された統計により、次のクエリの結果が潜在的に向上します。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT LastName, FirstName  
    FROM Person.Person  
    WHERE EmailPromotion = 2  
    ORDER BY LastName, FirstName;   
    GO  
    ```  
  
 詳細については、「[CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)」を参照してください。  
  
  
