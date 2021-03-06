---
title: setIntegratedSecurity メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setIntegratedSecurity
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2dca7a3c3cb2f6ac80fd9901c05e03135a42dc4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842868"
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>setIntegratedSecurity メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**integratedSecurity プロパティが有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *enable*  
  
 **true** integratedSecurity が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 設定"**true**"で Windows 資格情報を使用することを示すために[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]アプリケーションのユーザーを認証します。 場合"**true**"では、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]はローカル コンピューターの資格情報キャッシュをコンピューターまたはネットワーク ログオンで既に提供されている資格情報を検索します。 場合"**false**"、ユーザー名とパスワードを指定する必要があります。  
  
> [!NOTE]  
>  このプロパティでのみサポート[!INCLUDE[msCoName](../../../includes/msconame_md.md)]Windows オペレーティング システムです。  
  
 詳細については、統合認証を使用して、次を参照してください。[接続 URL の構築](../../../connect/jdbc/building-the-connection-url.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
