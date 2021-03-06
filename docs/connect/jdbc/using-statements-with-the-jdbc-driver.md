---
title: JDBC ドライバーでステートメントを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7da2ce5f69df8f28b281a935ea938b2648fa555
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851487"
---
# <a name="using-statements-with-the-jdbc-driver"></a>JDBC ドライバーでのステートメントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]でデータを操作するために使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]さまざまな方法でデータベース。 入力パラメーターや出力パラメーターを使用して、データベースに SQL ステートメントを実行したり、データベースのストアド プロシージャを呼び出したりできます。 JDBC ドライバーは、バッチ操作による SQL エスケープ シーケンス、更新数、自動生成キーの使用、および更新の実行もサポートしています。  
  
 JDBC ドライバーからのデータを取得するための 3 つのクラスの提供、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
1.  [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) - パラメーターなしの SQL ステートメントを実行するために使用されます。  
  
2.  [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) - (SQLServerStatement から継承された) IN パラメーターを含むコンパイル済みの SQL ステートメントが実行中のために使用します。  
  
3.  [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) - (SQLServerPreparedStatement から継承)、パラメーター、OUT パラメーター、またはその両方を含めることができるストアド プロシージャを実行するために使用します。  
  
 このセクションのトピックでは、これらの 3 つのステートメント クラスのデータの操作を使用する方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQL でのステートメントの使用](../../connect/jdbc/using-statements-with-sql.md)|JDBC ドライバーで SQL ステートメントを使用してデータを処理する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)|JDBC ドライバーでストアド プロシージャを使用してデータを処理する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[複数の結果セットの使用](../../connect/jdbc/using-multiple-result-sets.md)|JDBC ドライバーを使用して複数の結果セットからデータを取得する方法について説明します。|  
|[SQL エスケープ シーケンスの使用](../../connect/jdbc/using-sql-escape-sequences.md)|日付および時刻のリテラルや関数のような SQL エスケープ シーケンスの使用方法について説明します。|  
|[自動生成キーの使用](../../connect/jdbc/using-auto-generated-keys.md)|自動生成キーの使用方法について説明します。|  
|[バッチ操作の実行](../../connect/jdbc/performing-batch-operations.md)|JDBC ドライバーを使用してバッチ操作を行う方法について説明します。|  
|[複雑なステートメントの処理](../../connect/jdbc/handling-complex-statements.md)|JDBC ドライバーを使用して、さまざまなタスクを実行しさまざまな型のデータを返す複雑なステートメントを実行する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
