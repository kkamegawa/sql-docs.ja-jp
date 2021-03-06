---
title: SQLServerXAResource のメンバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36b5bc655f0ad54a8c326030aa123ef043920a13
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850957"
---
# <a name="sqlserverxaresource-members"></a>SQLServerXAResource のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
  
|名前|Description|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|XA ブランチ トランザクション ID (XID) は異なるが、グローバル トランザクション ID (GTRID) が同じである、密に結合された XA トランザクションを許可するために使用します。|  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN、TMFAIL、TMJOIN、TMNOFLAGS、TMONEPHASE、TMRESUME、TMSTARTRSCAN、TMSUCCESS、TMSUSPEND、XA_OK、XA_RDONLY|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|指定された Xid オブジェクトによって指定されたグローバル トランザクションをコミットします。|  
|[終わり](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|トランザクション ブランチのために実行していた処理を終了します。|  
|[忘れた](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|リソース マネージャーに対し、ヒューリスティックに決着されたトランザクション ブランチを無視するよう指示します。|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|値が現在のトランザクションのタイムアウト値を取得[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)オブジェクト。|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|ターゲット オブジェクトによって表されるリソース マネージャーのインスタンスが、渡された XAResource オブジェクトによって表されるリソース マネージャーのインスタンスと同じかどうかを判断します。|  
|[準備します。](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|リソース マネージャーが、渡された Xid オブジェクトによって指定されたトランザクションのトランザクション コミットの準備を要求します。|  
|[復元 (recover)](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|準備されたトランザクション ブランチの一覧を、リソース マネージャーから取得します。|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|トランザクション ブランチのために実行した処理をロールバックするように、リソース マネージャーに要求します。|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|現在のトランザクションのタイムアウト値を設定[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)オブジェクト。|  
|[start](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Xid オブジェクトで指定されたトランザクション ブランチのために処理を開始します。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
