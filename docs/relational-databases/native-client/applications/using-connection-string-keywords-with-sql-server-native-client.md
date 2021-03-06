---
title: SQL Server Native Client で接続文字列キーワードの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
caps.latest.revision: 81
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c30c279eb6c32d4c602ed8d6f27d91035001e6a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32957399"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>SQL Server Native Client での接続文字列キーワードの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  一部の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client API では、接続文字列を使用して接続属性を指定します。 接続文字列はキーワードとそれに関連する値のリストです。各キーワードによって特定の接続属性を識別します。  
  
> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]旧バージョンとの互換性を維持する接続文字列のあいまいさにより、ネイティブ クライアント (たとえば、いくつかのキーワードを複数回指定することがあり、位置に基づいて解像度で競合するキーワードを許可することがありますor の優先順位)。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の今後のリリースでは、あいまいな接続文字列を使用できなくなる可能性があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用するアプリケーションでは、あいまいな接続文字列を利用しないように変更することをお勧めします。  
  
 次のセクションでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をデータ プロバイダーとして使用するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、および ADO (ActiveX Data Objects) と共に使用できるキーワードについて説明します。  
  
## <a name="odbc-driver-connection-string-keywords"></a>ODBC ドライバー接続文字列キーワード  
 ODBC アプリケーションでは、接続文字列を使用するパラメーターとして、 [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)と[SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)関数。  
  
 ODBC で使用される接続文字列の構文を次に示します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて中かっこで囲むことができます。常に中かっこを使用すると、 属性値に英数字以外の文字が含まれる場合の問題を回避できます。 最初の右中かっこが値の終わりと見なされるため、値に右中かっこを含めることはできません。  
  
 次の表に、ODBC 接続文字列と共に使用できるキーワードを示します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|**addr**|"Address" のシノニム。|  
|**Address**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスを実行しているサーバーのネットワーク アドレス。 **アドレス**は通常、サーバーのネットワーク名が、パイプ、IP アドレス、または TCP/IP ポートとソケット アドレスなど他の名前を指定できます。<br /><br /> IP アドレスを指定する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認します。<br /><br /> 値**アドレス**に渡された値よりも優先**サーバー** ODBC 接続文字列を使用する場合に[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client です。 またを注意してください`Address=;`で指定したサーバーに接続する、**サーバー**キーワード、一方`Address= ;, Address=.;`、 `Address=localhost;`、および`Address=(local);`すべてが原因で、ローカル サーバーに接続します。<br /><br /> 完全な構文、**アドレス**キーワードのとおりです。<br /><br /> [*プロトコル ***:**]* アドレス *[* *、* * * ポート&#124;\pipe\pipename*]<br /><br /> *protocol* には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。 プロトコルの詳細については、次を参照してください。 [Configure Client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md)です。<br /><br /> どちらの場合*プロトコル*も**ネットワーク**キーワードを指定すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br /> *ポート*に接続する、指定したサーバー上のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。|  
|**AnsiNPW**|"yes" の場合、ANSI で定められた動作に従って NULL の比較、文字データの埋め込み、警告、および NULL 連結が処理されます。 "no" の場合、ANSI で定められた動作が公開されません。 ANSI NPW 動作の詳細については、次を参照してください。 [ISO オプションの効果](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)です。|  
|**APP**|呼び出すアプリケーションの名前[SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) (省略可能)。 この値が格納されている、指定した場合、 **master.dbo.sysprocesses**列**専用**によって返されると[sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)と[APP_NAME](../../../t-sql/functions/app-name-transact-sql.md)関数。|  
|**ApplicationIntent**|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。 既定値は**ReadWrite**です。  以下に例を示します。<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[SQL Server ネイティブ クライアントをサポートして高可用性、災害復旧](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。|  
|**AttachDBFileName**|アタッチできるデータベースのプライマリ ファイルの名前。 この名前には完全なパス名を指定します。また C 文字列変数を使用する場合は、\ 文字をエスケープしてください。<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> このデータベースがアタッチされ、接続の既定のデータベースとして使用されます。 使用する**AttachDBFileName**いずれかで、データベース名を指定することも必要があります、 [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) DATABASE パラメーターまたは SQL_COPT_CURRENT_CATALOG 接続属性。 データベースが以前にアタッチされていた場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] により再アタッチされることはありません (アタッチされたデータベースがその接続の既定のデータベースとして使用されます)。|  
|**AutoTranslate**|"yes" の場合、クライアントとサーバーの間で送受信される ANSI 文字列は、いったん Unicode に変換されます。これは、クライアントとサーバーのコード ページ間で拡張文字を照合するときに発生する問題を最小限に抑えるためです。<br /><br /> クライアントの SQL_C_CHAR データに送信される、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**、 **varchar**、または**テキスト**変数、パラメーター、または列が文字からクライアントの ANSI コード ページ (ACP) を使用して Unicode に変換して、サーバーの acp に基づいて文字を Unicode からに変換します。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**char**、 **varchar**、または**テキスト**クライアントの SQL_C_CHAR 変数に送信されるデータが文字からサーバーの acp に基づいてを使用して Unicode に変換し、クライアントの acp に基づいて文字を Unicode から変換します。<br /><br /> この変換は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーによってクライアントで行われます。 また、サーバーで使用しているものと同じ ACP (ANSI コード ページ) がクライアントでも使用可能になっている必要があります。<br /><br /> 次の設定は、送受信時の変換に影響しません。<br /><br /> \* 送信される Unicode の SQL_C_WCHAR クライアント データ**char**、 **varchar**、または**テキスト**サーバーにします。<br /><br /> \* **char**、 **varchar**、または**テキスト**サーバー データのクライアントの Unicode の SQL_C_WCHAR 変数に送信します。<br /><br /> \* Unicode に送信される ANSI SQL_C_CHAR クライアント データ**nchar**、 **nvarchar**、または**ntext**サーバーにします。<br /><br /> \* Unicode **nchar**、 **nvarchar**、または**ntext**サーバー データのクライアントの ANSI SQL_C_CHAR 変数に送信します。<br /><br /> "no" の場合、文字の変換は行われません。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでに送信されるクライアント ANSI 文字の SQL_C_CHAR データは変換されません**char**、 **varchar**、または**テキスト**変数、パラメーター、またはサーバー上の列です。 変換は実行されません**char**、 **varchar**、または**テキスト**クライアントの SQL_C_CHAR 変数に、サーバーから送信されるデータ。<br /><br /> クライアントと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で使用する ACP が異なる場合、拡張文字の解釈が正しく行われない場合があります。|  
|**データベース**|接続に使用する既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースの名前。 場合**データベース**が指定されていない、ログインに対して定義されている既定のデータベースを使用します。 ODBC データ ソースの既定のデータベースは、ログインに定義されている既定のデータベースよりも優先されます。 データベースは、しない限り、既存のデータベースにする必要があります**AttachDBFileName**も指定されています。 場合**AttachDBFileName**も指定すると、プライマリ ファイルを指しているがアタッチされ、によって指定されたデータベース名を指定**データベース**です。|  
|**[ドライバー]**|によって返されるドライバー名[SQLDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md)です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに対するこのキーワードの値は "{SQL Server Native Client 11.0}" です。 **サーバー**キーワードは必要な場合**ドライバー**が指定されていると**DriverCompletion**を SQL_DRIVER_NOPROMPT に設定します。<br /><br /> ドライバー名の詳細については、次を参照してください。 [SQL Server Native Client ヘッダーとライブラリ ファイルを使用して](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)です。|  
|**DSN**|既存の ODBC ユーザー データ ソースまたはシステム データ ソースの名前。 このキーワードで指定されている任意の値を上書きします。、**サーバー**、**ネットワーク**、および**アドレス**キーワード。|  
|**Encrypt**|データをネットワークに送信する前に暗号化するかどうかを指定します。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**フォールバック**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、このキーワードは推奨されず、設定は無視されます。|  
|**Failover_Partner**|プライマリ サーバーに接続できない場合に使用するフェールオーバー パートナー サーバーの名前。|  
|**FailoverPartnerSPN**|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はドライバーが生成した SPN を既定値として使用します。|  
|**FileDSN**|既存の ODBC ファイル データ ソースの名前。|  
|**言語**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前 (省略可)。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]複数の言語のメッセージを格納できます**sysmessages**です。 接続する場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で複数の言語、**言語**接続の使用は、メッセージのセットを指定します。|  
|**MARS_Connection**|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします。 認識できる値は "yes" と "no" です。 既定値は"no"です。|  
|**MultiSubnetFailover**|常に指定**multiSubnetFailover = [はい]** の可用性グループ リスナーに接続するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可用性グループ、または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス。 **multiSubnetFailover = [はい]** 構成[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client を迅速に検出し、(現在) アクティブなサーバーへの接続を提供します。 可能な値は **Yes** と **No**です。 既定値は**いいえ**です。 以下に例を示します。<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[SQL Server ネイティブ クライアントをサポートして高可用性、災害復旧](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。|  
|**net**|"Network" のシノニム。|  
|**ネットワーク**|有効な値は**dbnmpntw** (名前付きパイプ) と**dbmssocn** (TCP/IP)。<br /><br /> 両方の値を指定すると、エラーは、**ネットワーク**キーワードと、プロトコル プレフィックスの**サーバー**キーワード。|  
|**PWD**|UID パラメーターで指定されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン アカウントのパスワード。 **PWD**いない指定する必要は、ログインのパスワードは NULL の場合、または Windows 認証を使用する場合 (`Trusted_Connection = yes`)。|  
|**QueryLog_On**|"yes" の場合、その接続では、実行時間の長いクエリのデータに関するログを記録できます。 "no" の場合、実行時間の長いクエリのデータに関するログは記録されません。|  
|**QueryLogFile**|実行時間の長いクエリのデータをログに記録する場合に使用するファイルの完全なパスとファイル名。|  
|**QueryLogTime**|実行時間の長いクエリをログに記録するためのしきい値 (ミリ秒) を指定する数字文字列。 指定時間内に応答が返ってこないクエリは、実行時間の長いクエリ用のログ ファイルに記録されます。|  
|**QuotedId**|"yes" の場合、その接続の QUOTED_IDENTIFIERS が ON に設定され、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は ISO 規則に従って SQL ステートメントの引用符を処理します。 "no" の場合、その接続の QUOTED_IDENTIFIERS が OFF に設定され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は従来の [!INCLUDE[tsql](../../../includes/tsql-md.md)] 規則に従って SQL ステートメントの引用符を処理します。 詳細については、次を参照してください。 [ISO オプションの効果](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)です。|  
|**地域**|"yes" の場合、通貨、日付、および時刻データが文字データに変換されるときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーではクライアントの設定が使用されます。 変換は一方向にのみ行われます。INSERT ステートメントや UPDATE ステートメントのパラメーターなどで日付文字列または通貨の値が ODBC 標準以外の形式で指定されている場合、ドライバーでは、これらの値は認識されません。 "no" の場合、文字データに変換される通貨、日付、および時刻データを表現するために ODBC 標準の文字列が使用されます。|  
|**SaveFile**|接続が成功した場合に、現在の接続の属性を保存する ODBC データ ソース ファイルの名前。|  
|**[サーバー]**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。 ネットワーク上のサーバーの名前、IP アドレス、または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーの別名を指定する必要があります。<br /><br /> **アドレス**キーワードよりも優先、**サーバー**キーワード。<br /><br /> ローカル サーバーの既定のインスタンスに接続するには、次のいずれかを指定します。<br /><br /> **サーバー = です。**<br /><br /> **サーバー =。 です。**<br /><br /> **Server=(local) です。**<br /><br /> **Server=(local) です。**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *instancename* **;**<br /><br /> LocalDB のサポートの詳細については、次を参照してください。 [SQL Server ネイティブ クライアントのサポート LocalDB](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)です。<br /><br /> 名前付きインスタンスを指定する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、追加 **\\ ***InstanceName*です。<br /><br />サーバーが指定されていない場合、ローカル コンピューター上の既定のインスタンス、接続を確立します。<br /><br />IP アドレスを指定する場合で TCP/IP または名前付きパイプ プロトコルが有効になっていることを確認してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br />完全な構文、**サーバー**キーワードのとおりです:<br /> <br /> **サーバー =**[* プロトコル***:**]*サーバー*[**、* * * ポート*]<br /><br /> *protocol* には、 **tcp** (TCP/IP)、 **lpc** (共有メモリ)、または **np** (名前付きパイプ) を指定できます。<br /><br /> 名前付きパイプを指定する例を次に示します。<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> この行では、名前付きパイプのプロトコル、ローカル コンピューター上の名前付きパイプ (`\\.\pipe`)、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前 (`MSSQL$MYINST01`)、および名前付きパイプの既定の名前 (`sql/query`) を指定しています。<br /><br /> どちらの場合、*プロトコル*も**ネットワーク**キーワードを指定すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client がで指定されたプロトコルの順序を使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager です。<br /><br /> *ポート*に接続する、指定したサーバー上のポートです。 既定では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はポート 1433 を使用します。<br /><br /> 渡される値の先頭のスペースは無視されます**サーバー** ODBC 接続文字列を使用する場合に[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client です。|  
|**ServerSPN**|サーバーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はドライバーが生成した SPN を既定値として使用します。|  
|**StatsLog_On**|"yes" の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのパフォーマンス データをキャプチャできます。 "no" の場合、その接続では [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのパフォーマンス データを取得できません。|  
|**StatsLogFile**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのパフォーマンス統計を記録するために使用するファイルの完全なパスとファイル名。|  
|**Trusted_Connection**|"yes" の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでログインを検証するときに Windows 認証モードが使用されます。 それ以外の場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでログインを検証するときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザー名とパスワードが使用され、UID キーワードと PWD キーワードの指定が必要になります。|  
|**TrustServerCertificate**|使用すると**暗号化**、自己署名サーバー証明書を使用して暗号化を有効にします。|  
|**UID**|有効な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン アカウント。 Windows 認証を使用する場合は UID を指定する必要はありません。|  
|**UseProcForPrepare**|このキーワードは廃止され、によってその設定は無視されます、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。|  
|**WSID**|ワークステーション ID。 通常は、アプリケーションが実装されているコンピューターのネットワーク名です (省略可)。 この値が格納されている、指定した場合、 **master.dbo.sysprocesses**列**hostname**によって返されると[sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)と[HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md)関数。|  
  
> **注:** 地域別の変換の設定は、通貨、数値、日付、および時刻のデータ型に適用します。 変換の設定は、出力変換にのみ適用され、通貨、数値、日付、または時刻の値を文字列に変換する場合にのみ確認することができます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、現在のユーザーに関するロケールのレジストリ設定が使用されます。 アプリケーション設定、接続後を呼び出す場合、ドライバーは現在のスレッドのロケールを認めません**SetThreadLocale**です。  
  
 データ ソースの地域別の動作を変更すると、アプリケーション エラーが発生することがあります。 日付文字列を解析し、ODBC の定義に従った形式の日付文字列を受け付けるアプリケーションが、地域別の動作の値を変更することによって、悪影響を受ける可能性があります。  
  
## <a name="ole-db-provider-connection-string-keywords"></a>OLE DB プロバイダーの接続文字列キーワード  
 OLE DB アプリケーションでデータ ソース オブジェクトを初期化する方法は 2 つあります。  
  
-   **Idbinitialize::initialize**  
  
-   **Idatainitialize::getdatasource**  
  
 最初の方法では、DBPROPSET_DBINIT プロパティ セットのプロパティ DBPROP_INIT_PROVIDERSTRING を設定することにより、プロバイダー文字列で接続プロパティを初期化できます。 2 番目のケースでは、初期化文字列に渡せる**idatainitialize::getdatasource**接続のプロパティを初期化します。 いずれの方法でも同一の OLE DB 接続プロパティが初期化されますが、使用されるキーワードのセットは異なります。 使用されるキーワードのセット**idatainitialize::getdatasource**が最小 initialization プロパティ グループ内のプロパティの説明。  
  
 対応する OLE DB プロパティを持つプロバイダー文字列の設定は一部の既定値に設定されるか、値に明示的に設定され、OLE DB プロパティ値はプロバイダー文字列の設定をオーバーライドします。  
  
 DBPROP_INIT_PROVIDERSTRING 値によってプロバイダー文字列内で設定されるブール型のプロパティは、値 "yes" と "no" を使用して設定します。 使用して初期化文字列に設定するブール型プロパティ**idatainitialize::getdatasource**値"true"および"false"を使用して設定されます。  
  
 使用してアプリケーション**idatainitialize::getdatasource**で使用されるキーワードを使用することも**idbinitialize::initialize**が既定値を持たないプロパティに対してのみです。 アプリケーションでは、どちらも使用している場合、 **idatainitialize::getdatasource**キーワードおよび**idbinitialize::initialize**初期化文字列のキーワードで、 **idatainitialize::getdatasource**キーワードの設定を使用します。 アプリケーションが使用しないことを強くお勧め**idbinitialize::initialize**キーワード**IDataInitialize:GetDataSource**接続文字列をこの動作が維持されない将来のリリースとします。  
  
> [!NOTE]  
>  接続文字列を通過**idatainitialize::getdatasource**プロパティに変換され、使用して適用**idbproperties::setproperties**です。 コンポーネント サービスのプロパティの説明が見つかった場合 **:getpropertyinfo**、このプロパティはスタンドアロン プロパティとして適用されます。 それ以外の場合は、DBPROP_PROVIDERSTRING プロパティを介して適用されます。 たとえば、接続文字列を指定する**データ ソース = server1 です。Server = server2**、**データ ソース**をプロパティとして設定されますが、**サーバー**プロバイダー文字列に変わります。  
  
 同じプロバイダー固有のプロパティの複数のインスタンスを指定する場合、最初のプロパティの最初の値が使用されます。  
  
 と共に DBPROP_INIT_PROVIDERSTRING を使用して OLE DB アプリケーションで使用される接続文字列**idbinitialize::initialize**次の構文します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて中かっこで囲むことができます。常に中かっこを使用すると、 属性値に英数字以外の文字が含まれる場合の問題を回避できます。 最初の右中かっこが値の終わりと見なされるため、値に右中かっこを含めることはできません。  
  
 値が引用符で囲まれている場合でも、リテラルとして解釈されます、接続文字列キーワードの等号 (=) 後のスペース文字。  
  
 次の表に、DBPROP_INIT_PROVIDERSTRING と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**addr**|SSPROP_INIT_NETWORKADDRESS|"Address" のシノニム。|  
|**Address**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**アドレス**ODBC キーワードは、このトピックで後述します。|  
|**APP**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[SQL Server ネイティブ クライアントをサポートして高可用性、災害復旧](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の Database キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "yes" と "no" です。|  
|**データベース**|DBPROP_INIT_CATALOG|データベース名です。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語。|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 有効値は、"yes" および "no" です。 既定値は "no" です。|  
|**net**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**ネットワーク**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|"Network" のシノニム。|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "yes" と "no" を値として受け取ります。 "no" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**PWD**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**[サーバー]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**サーバー** ODBC キーワードは、このトピックの「します。|  
|**ServerSPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|"yes" の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでログインを検証するときに Windows 認証モードが使用されます。 それ以外の場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでログインを検証するときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザー名とパスワードが使用され、UID キーワードと PWD キーワードの指定が必要になります。|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "yes" と "no" を値として受け取ります。 既定値は "no" です。これはサーバー証明書が検証されることを示します。|  
|**UID**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、このキーワードは推奨されず、設定は無視されます。|  
|**WSID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 使用して OLE DB アプリケーションで使用される接続文字列**idatainitialize::getdatasource**次の構文します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 プロパティの使用方法は、プロパティのスコープで許可される構文に従っている必要があります。  たとえば、 **WSID**中かっこを使用して (**{}**) 引用符の文字と**アプリケーション名**では一重 (**'**) または二重 (**"**) 引用符文字。 引用符で囲むことができるのは、文字列のプロパティのみです。 整数または列挙のプロパティを引用符で囲むと、"接続文字列は OLE DB 仕様に準拠していません" というエラーが発生します。  
  
 属性値は必要に応じて一重引用符または二重引用符で囲むことができます。常にこれらの引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 二重引用符の場合は、値の中に含めることもできます。  
  
 値が引用符で囲まれている場合でも、リテラルとして解釈されます、接続文字列キーワードの等号 (=) 後のスペース文字。  
  
 接続文字列に次の表のプロパティが複数含まれている場合は、最後のプロパティの値が使用されます。  
  
 次の表に、キーワードと共に使用できるを**idatainitialize::getdatasource**:  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**アプリケーションの目的**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[SQL Server ネイティブ クライアントをサポートして高可用性、災害復旧](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**現在の言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**サーバー** ODBC キーワードは、このトピックで後述します。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|データ型を使用する処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**フェールオーバー パートナー SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の DATABASE キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS 接続**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします。 認識できる値は "true" と "false" です。 既定値は "false" です。|  
|**ネットワーク アドレス**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**アドレス**ODBC キーワードは、このトピックで後述します。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**Password**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 機微な認証情報を保持するデータ ソース オブジェクトが許可されていません"false"の場合|  
|**プロバイダー**||[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の場合は "SQLNCLI11"。|  
|**サーバーの SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**[Trust Server Certificate]**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は"false"です。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**ワークステーション ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 **注**接続文字列で"Old Password"プロパティを設定 SSPROP_AUTH_OLD_PASSWORD、これは、現在 (または期限切れの) はないパスワードをプロバイダー文字列のプロパティ経由で入手できます。  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>ADO (ActiveX Data Objects) の接続文字列のキーワード  
 ADO アプリケーション セット、 **ConnectionString**プロパティの**ADODBConnection**オブジェクトまたはパラメーターとして接続文字列を指定、**開く**メソッドの**ADODBConnection**オブジェクト。  
  
 ADO アプリケーションでは、OLE DB で使用されるキーワードを使用できますも**idbinitialize::initialize**メソッドは、既定値がないプロパティについては、します。 アプリケーションが ADO キーワードを使用する場合、 **idbinitialize::initialize**初期化文字列、ADO キーワードの設定でキーワードが使用されます。 アプリケーションでは ADO 接続文字列のキーワードのみを使用することを強くお勧めします。  
  
 ADO で使用される接続文字列の構文を次に示します。  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 属性値は必要に応じて二重引用符で囲むことができます。常に二重引用符を使用すると、 値に英数字以外の文字が含まれる場合の問題を回避できます。 属性値に二重引用符を含めることはできません。  
  
 次の表に、ADO 接続文字列と共に使用できるキーワードを示します。  
  
|Keyword|初期化プロパティ|Description|  
|-------------|-----------------------------|-----------------|  
|**アプリケーションの目的**|SSPROP_INIT_APPLICATIONINTENT|アプリケーションがサーバーに接続するときのワークロードのタイプを宣言します。 指定できる値は**ReadOnly**と**ReadWrite**です。<br /><br /> 既定値は**ReadWrite**です。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client のサポート[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]を参照してください[SQL Server ネイティブ クライアントをサポートして高可用性、災害復旧](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)です。|  
|**Application Name**|SSPROP_INIT_APPNAME|アプリケーションを識別する文字列。|  
|**Auto Translate します。**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" のシノニム。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|OEM/ANSI 文字の変換を構成します。 認識できる値は "true" と "false" です。|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|データ ソースの初期化が完了するのを待機する秒数。|  
|**現在の言語**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 言語の名前。|  
|**[データ ソース]**|DBPROP_INIT_DATASOURCE|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの名前。<br /><br /> 指定されなかった場合は、ローカル コンピューター上にある既定のインスタンスに接続します。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**サーバー** ODBC キーワードは、このトピックの「します。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|使用するデータ型処理モードを指定します。 認識できる値は、プロバイダー データ型を示す "0" および SQL Server 2000 データ型を示す "80" です。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|データベース ミラーリングに使用するフェールオーバー サーバーの名前。|  
|**フェールオーバー パートナー SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|フェールオーバー パートナーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**初期カタログ**|DBPROP_INIT_CATALOG|データベース名です。|  
|**初期ファイル名**|SSPROP_INIT_FILENAME|アタッチできるデータベースのプライマリ ファイルの名前 (完全なパス名を含む)。 使用する**AttachDBFileName**、プロバイダー文字列の DATABASE キーワードでデータベース名を指定することも必要があります。 場合は、データベースは、以前にアタッチされて、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に再アタッチしません (、アタッチされたデータベースの既定値として接続に使用)。|  
|**統合セキュリティ**|DBPROP_AUTH_INTEGRATED|Windows 認証の値 "SSPI" を受け取ります。|  
|**MARS 接続**|SSPROP_INIT_MARSCONNECTION|その接続で MARS (複数のアクティブな結果セット) を有効または無効にします ([!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のサーバーの場合)。 認識できる値は "true" と "false" です。既定値は "false" です。|  
|**ネットワーク アドレス**|SSPROP_INIT_NETWORKADDRESS|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのネットワーク アドレス。<br /><br /> 有効なアドレス構文の詳細については、の説明を参照して、**アドレス**ODBC キーワードは、このトピックの「します。|  
|**ネットワーク ライブラリ**|SSPROP_INIT_NETWORKLIBRARY|組織内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立するために使用するネットワーク ライブラリ。|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|ネットワーク パケットのサイズ。 既定値は 4096 です。|  
|**Password**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン パスワード。|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|文字列 "true" と "false" を値として受け取ります。 "false" の場合、データ ソース オブジェクトには機密の認証情報を保存できません。|  
|**プロバイダー**||[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の場合は "SQLNCLI11"。|  
|**サーバーの SPN**|SSPROP_INIT_SERVERSPN|サーバーの SPN。 既定値は空の文字列です。 空の文字列の場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はプロバイダーが生成した SPN を既定値として使用します。|  
|**[Trust Server Certificate]**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|文字列 "true" と "false" を値として受け取ります。 既定値は "false" です。これはサーバー証明書が検証されることを示します。|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|データをネットワークに送信する前に暗号化するかどうかを指定します。 指定できる値は "true" と "false" です。 既定値は"false"です。|  
|**[ユーザー ID]**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン名。|  
|**ワークステーション ID**|SSPROP_INIT_WSID|ワークステーションの識別子です。|  
  
 **注**接続文字列で"Old Password"プロパティを設定 SSPROP_AUTH_OLD_PASSWORD、これは、現在 (または期限切れの) はないパスワードをプロバイダー文字列のプロパティ経由で入手できます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client でアプリケーションの構築](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
