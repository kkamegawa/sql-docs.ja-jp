---
title: 複数のアクティブな結果セット (MARS) の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
caps.latest.revision: 56
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bd644f769d63af164aea238f657253cfd32bbb33
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32955777"
---
# <a name="using-multiple-active-result-sets-mars"></a>複数のアクティブな結果セット (MARS) の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] アクセスするアプリケーションで複数のアクティブな結果セット (MARS) のサポートが導入された、[!INCLUDE[ssDE](../../../includes/ssde-md.md)]です。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、データベース アプリケーションは 1 つの接続で複数のアクティブなステートメントを保持できませんでした。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定の結果セットを使用しているときは、アプリケーションはその接続で他のバッチを実行する前に、1 つのバッチのすべての結果セットを処理するか、取り消す必要がありました。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では新しい接続属性が導入され、アプリケーションは接続ごとに複数の要求を保留中にできるだけでなく、接続ごとに複数のアクティブな既定の結果セットを保持できるようになりました。  
  
 MARS によって、次の新しい機能を使用したアプリケーションのデザインが簡素化されます。  
  
-   アプリケーションは、既定の結果セットを複数開くことができ、複数の既定の結果セットからの読み取りをインターリーブすることができます。  
  
-   アプリケーションは既定の結果セットを開いたまま、他のステートメント (INSERT、UPDATE、DELETE、ストアド プロシージャ呼び出しなど) を実行できます。  
  
 MARS を使用するアプリケーションについては、次のガイドラインを参照してください。  
  
-   1 つの SQL ステートメント (SELECT、OUTPUT を伴う DML、RECEIVE、READ TEXT など) で生成される結果セットが短期間しか有効でない場合や結果セットが小さい場合は、既定の結果セットを使用します。  
  
-   1 つの SQL ステートメントで生成される結果セットが長期間有効な場合や結果セットが大きくなる場合は、サーバー カーソルを使用します。  
  
-   結果を返すかどうかにかかわらず手続き型の要求の場合、および複数の結果を返すバッチの場合、常に、結果の最後まで読み取ります。  
  
-   接続プロパティの変更やトランザクションの管理には、できるだけ [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントではなく API 呼び出しを優先して使用します。  
  
-   MARS では、複数のバッチが同時に実行されている間、セッション スコープの権限の借用が禁止されます。  
  
> [!NOTE]  
>  既定では、MARS 機能は有効になっていません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続するときに MARS を使用するには、接続文字列で MARS を明示的に有効にする必要があります。 詳細については、この後の「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー」と「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client では、接続でのアクティブなステートメントの数は制限されません。  
  
 複数のステートメントで構成される単一のバッチやストアド プロシージャを複数同時実行する必要のない一般的なアプリケーションでは、MARS の実装方法を理解しなくても、MARS の利点を得ることができます。 ただし、より複雑な要件のアプリケーションでは、MARS の実装方法を考慮する必要があります。  
  
 MARS では、1 つの接続内で複数の要求の実行をインターリーブできます。 つまり、1 つのバッチを実行し、その実行内で他の要求を実行できます。 ただし、MARS では並列実行が行われるのではなく、複数の実行がインターリーブされることに注意してください。  
  
 MARS のインフラストラクチャでは、複数のバッチがインターリーブ方式で実行されますが、実行の切り替えは明確に定義された時点でしか行われません。 また、ほとんどのステートメントはバッチ内で自動的に実行される必要があります。 ステートメントと呼ばクライアントに行を返す*呼び出しポイント*行に送信される、クライアントでは、たとえば中に完了する前に実行をインターリーブする許可。  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 ストアド プロシージャまたはバッチの一部として実行されるその他のステートメントはいずれも、他の MARS 要求に切り替えられる前に実行を完了する必要があります。  
  
 バッチがどのようにインターリーブ実行されるかは、さまざまな要因の影響を受けます。そのため、呼び出しポイントを含む複数のバッチからのコマンドが実行されるときに、正確なシーケンスを予測することは困難です。 このような複雑なバッチをインターリーブ実行したときに、好ましくない影響が発生しないように注意してください。  
  
 このような問題を回避するために、接続状態 (SET、USE) やトランザクション (BEGIN TRAN、COMMIT、ROLLBACK) を管理する場合は、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントではなく API 呼び出しを使用します。このとき、複数のステートメントで構成されるバッチに呼び出しポイントも含まれている場合、接続状態やトランザクションを管理するステートメントを含めないようにします。さらに、このようなバッチでは、すべての結果を処理するか、残りを取り消すことによって、実行を順番に行います。  
  
> [!NOTE]  
>  MARS が有効なときにトランザクションを手動または暗黙に開始するバッチやストアド プロシージャでは、バッチが終了する前にトランザクションを完了する必要があります。 トランザクションを完了しないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はバッチの終了時にトランザクションによって行われたすべての変更をロールバックします。 このようなトランザクションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によってバッチスコープのトランザクションとして管理されます。 これは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入された新しい形式のトランザクションで、MARS が有効なときに、既存の適切に動作するストアド プロシージャを使用できるようになります。 バッチ スコープのトランザクションの詳細については、次を参照してください。 [Transaction ステートメント&#40;TRANSACT-SQL&#41;](~/t-sql/statements/statements.md)です。  
  
 ADO から MARS を使用しての例は、次を参照してください。 [SQL Server Native Client と ADO を使用する](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md)です。  
  
## <a name="in-memory-oltp"></a>インメモリ OLTP  
 インメモリ OLTP では、クエリを使用して MARS をサポートし、ネイティブ コンパイル ストアド プロシージャ。 MARS は、完全に各結果を新しい結果セットから行をフェッチする要求を送信する前にセットを取得することがなく複数のクエリからデータを要求するを使用できます。 正常に開いている複数の結果から読み取ることは、セット、MARS を使用する必要がありますには、接続が有効になります。  
  
 MARS は既定で無効に追加することで明示的に有効にする必要がありますので`MultipleActiveResultSets=True`接続文字列にします。 次の例では、SQL Server のインスタンスに接続し、MARS が有効になっていることを指定する方法を示します。  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 MARS のインメモリ OLTP では、本質的に MARS と同じ SQL エンジンの残りの部分。 次に示します MARS を使用してメモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャとの相違点を。  
  
 **MARS とメモリ最適化テーブル**  
  
 ディスク ベース テーブルとメモリ最適化テーブル、MARS を使用して、接続が有効になっている間の相違点を次に示します。  
  
-   書き込み-書き込み競合新しい操作が失敗すると、同じレコードを変更しようとすると、両方は 2 つのステートメントは、同じターゲット オブジェクトのデータを変更できます。 ただし、両方の操作は、別のレコードを変更する場合、操作は成功します。  
  
-   各ステートメントは、新しい操作が既存のステートメントによって行われた変更を確認できないように、SNAPSHOT 分離で実行されます。 同時実行のステートメントが同じトランザクションで実行された場合でも、SQL エンジンはバッチ スコープのトランザクションの各ステートメントに対して互いから分離されるを作成します。 ただし、バッチ スコープのトランザクションはまだ結びつけたため同じバッチ内の他のものが 1 つのバッチ スコープのトランザクションのロールバックに影響します。  
  
-   ユーザー トランザクションでは DDL 操作は許可されていないのでがすぐに失敗します。  
  
 **MARS およびネイティブ コンパイル ストアド プロシージャ**  
  
 ネイティブ コンパイル ストアド プロシージャは、MARS が有効になっている接続で実行し、降伏点が発生した場合にのみの別のステートメントの実行が明け渡さことができます。 Yield ポイントには、別のステートメントの実行を生成するネイティブ コンパイル ストアド プロシージャ内の唯一のステートメントは、SELECT ステートメントが必要です。 SELECT ステートメントが生成は、プロシージャに存在しない場合は、その他のステートメントの開始前に完了するまで実行されます。  
  
 **MARS とインメモリ OLTP でのトランザクション**  
  
 ステートメントおよびはインターリーブされます。 atomic ブロックによって行われた変更は、互いに分離されます。 たとえば、1 つのステートメントまたは atomic ブロックは、いくつかの変更を行い、別のステートメントの実行を譲歩する場合、新しいステートメントは、最初のステートメントによって行われた変更は表示されません。 さらに、最初のステートメントが実行を再開するときは、確認されません他のどのステートメントによって行われた変更します。 ステートメントは、終了され、ステートメントが開始される前にコミットされる変更にのみ表示されます。  
  
 BEGIN TRANSACTION ステートメントを使用して、現在のユーザー トランザクション内で新しいユーザー トランザクションを開始できます: これは、BEGIN TRANSACTION は、T-SQL ステートメントからのみ呼び出すことができますので、相互運用モードでのみサポートされてからネイティブ コンパイルで保存されていません。プロシージャです。セーブポイントを作成することができますで SAVE TRANSACTION またはトランザクションへの API 呼び出しを使用してトランザクションにします。セーブポイントにロールバックする Save(save_point_name) です。 この機能は、T-SQL ステートメントからのみ有効になりますからではなく内でネイティブ コンパイル ストアド プロシージャ。  
  
 **MARS および列ストア インデックス**  
  
 SQL Server (2016年以降) には、列ストア インデックスで MARS がサポートされています。 SQL Server 2014 では、列ストア インデックスに読み取り専用で接続するために MARS が使用されます。    ただし、SQL Server 2014 では、列ストア インデックスを含むテーブルで DML (データ操作言語) を同時操作するとき、MARS を利用できません。 この場合、SQL Server がの接続を終了し、トランザクションを中止します。   SQL Server 2012 は読み取り専用の列ストア インデックスを持ち、MARS は、それらには適用されません。  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBPROPSET_SQLSERVERDBINIT プロパティ セットに実装される SSPROP_INIT_MARSCONNECTION データ ソース初期化プロパティの追加によって MARS をサポートしています。 さらに、新しい接続文字列のキーワード**MarsConn**で追加されました。 受け取って**true**または**false**値です。**false**既定値です。  
  
 データ ソース プロパティ DBPROP_MULTIPLECONNECTIONS の既定値は VARIANT_TRUE です。 これは、複数の同時実行コマンドや行セット オブジェクトをサポートするために、プロバイダーが複数の接続を起動することを意味しています。 MARS を有効にすると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、MULTIPLE_CONNECTIONS が既定で VARIANT_FALSE に設定されているために、単一の接続での複数のコマンドや行セット オブジェクトをサポートできます。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットへの拡張機能の詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a>SQL Server Native Client OLE DB プロバイダーの例  
 この例では、データ ソース オブジェクトが作成を使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native OLE DB プロバイダーと MARS が有効になっているセッション オブジェクトが作成される前に、設定、DBPROPSET_SQLSERVERDBINIT プロパティを使用します。  
  
```  
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーへの追加によって MARS をサポートしています、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)と[SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)関数。 SQL_COPT_SS_MARS_ENABLED が追加され、SQL_MARS_ENABLED_YES または SQL_MARS_ENABLED_NO を受け取ります。既定値は SQL_MARS_ENABLED_NO です。 さらに、新しい接続文字列のキーワード**Mars_Connection**で追加されました。 このキーワードは、"yes" と "no" を値として受け取ります。既定値は "no" です。  
  
### <a name="sql-server-native-client-odbc-driver-example"></a>SQL Server Native Client ODBC ドライバーの例  
 この例では、 **SQLSetConnectAttr**を呼び出す前に、MARS を有効にする関数が使用される、 **SQLDriverConnect**関数は、データベースに接続します。 接続が確立されると、2 つ**SQLExecDirect**関数は、同じ接続で 2 つの別の結果セットを作成すると呼ばれます。  
  
```  
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L”SELECT * FROM Authors”, SQL_NTS);  
SQLExecDirect(hstmt2, L”SELECT * FROM Titles”, SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [SQL Server の既定の結果セットの使用](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  
