---
title: テーブル値パラメーターを構成する列の記述子フィールド |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0b86145c43b072361b20d1e7e8869091689fb831
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32946577"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>テーブル値パラメーターを構成する列の記述子フィールド
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このセクションで説明するテーブル値パラメーターの記述子フィールドが使用して、操作は[SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)と[SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)実装パラメーター記述子 (のハンドルを持つIPD)。  
  
## <a name="remarks"></a>解説  
 SQL_DESC_AUTO_UNIQUE_VALUE は、その他の機能と同様にテーブル値パラメーターで使用されます。  
  
|属性名|型|Description|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE はこの列が ID 列であることを示します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パフォーマンスを最適化するためにこの情報を使用できますが、アプリケーションが id 列に設定する必要はありません。|  
  
 アプリケーション パラメーター記述子 (APD) および実装パラメーター記述子 (IPD) のすべてのパラメーターの型に追加される属性を次に示します。  
  
|属性名|型|Description|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE はこの列が計算列であることを示します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パフォーマンスを最適化するためにこの情報を使用できますが、アプリケーションは、計算列に設定する必要はありません。<br /><br /> テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE はテーブル値パラメーターの列が一意キーに参加することを示します。 これにより、クエリのパフォーマンスが向上します。 テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|テーブル値パラメーターの列の並べ替え順を示します。 これにより、クエリのパフォーマンスが向上します。 テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。 使用できる値を次に示します。 <br />**SQL_SS_ASCENDING_ORDER**<br />**SQL_SS_DESCENDING_ORDER**<br />**SQL_SS_ORDER_UNSPECIFIED**<br /><br /> 以外の値**SQL_SS_ASCENDING_ORDER**と**SQL_SS_DESCENDING_ORDER**でエラーが発生**SQLSTATE HY024**メッセージ '無効な属性の値' とはとして扱われます**SQL_SS_ORDER_UNSPECIFIED**がこの属性の既定値です。|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|テーブル値パラメーターの全体的な順序を定義する列セット内における、テーブル値パラメーター列の序数を示します。 これにより、クエリのパフォーマンスが向上します。 テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。 並べ替えの序数は 1 から始まります。 値が 0 (既定値) の場合は、テーブル値パラメーターの列に列の順序が設定されていないことを示します。|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|テーブル値パラメーターのすべての行にこの列の既定値が設定されるかどうかを示します。 テーブル値パラメーターの場合、行ごとに既定値を選択できません。 値が SQL_FALSE の場合は、行に既定値以外の値が設定されることを示します。 これは既定値です。 値が SQL_TRUE の場合は、この列のすべての行に既定値が設定されることを示します。<br /><br /> SQL_TRUE に設定されている場合、データはサーバーに送信されません。<br /><br /> 列の値がサーバー処理で不要な場合、このフィールドは ID 列または計算列でも使用することができます。|  
  
 これらの属性は、テーブル値パラメーターの列に対してのみ有効です。 他のパラメーターでは無視されます。  
  
 テーブル値パラメーターの列に SQL_CA_SS_COL_HAS_DEFAULT_VALUE を設定する場合は、その列の SQL_DESC_DATA_PTR が NULL ポインターである必要があります。 それ以外の場合、SQLExecute または SQLExecDirect は SQL_ERROR を返します。 Sqlstate 診断レコードが生成されます = 07S01 メッセージ"パラメーターの既定のパラメーターが正しく使用\<p >、列\<c >"ここで、 \<p > は、パラメーターの序数と\<c > は、列の序数。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
