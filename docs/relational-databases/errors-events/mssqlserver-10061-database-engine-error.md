---
title: MSSQLSERVER_10061 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5e5961d26fcc9e03abe383204d7cf737d6a8bbf
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321833"
---
# <a name="mssqlserver10061"></a>MSSQLSERVER_10061
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10061|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名||  
|メッセージ テキスト|サーバーへの接続を確立中にエラーが発生しました。  SQL Server に接続している場合、既定の設定では SQL Server によるリモート接続が許可されていないために、このエラーが発生した可能性があります。 (プロバイダー: TCP プロバイダー、エラー: 0 - 対象のコンピューターによって拒否されたため、接続できませんでした。) (Microsoft SQL Server、エラー: 10061)|  
  
## <a name="explanation"></a>説明  
サーバーがクライアント要求に応答しませんでした。 このエラーは、サーバーが起動していないことが原因で発生する可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
サーバーが起動していることを確認します。  
  
## <a name="see-also"></a>参照  
[データベース エンジン サービスの管理](~/database-engine/configure-windows/manage-the-database-engine-services.md)  
[クライアント プロトコルの構成](~/database-engine/configure-windows/configure-client-protocols.md)  
[ネットワーク プロトコルとネットワーク ライブラリ](~/sql-server/install/network-protocols-and-network-libraries.md)  
[クライアント ネットワーク構成](~/database-engine/configure-windows/client-network-configuration.md)  
[クライアント プロトコルの構成](~/database-engine/configure-windows/configure-client-protocols.md)  
[サーバー ネットワーク プロトコルの有効化または無効化](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
