---
title: sysmail_mailattachments (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_mailattachments_TSQL
- sysmail_mailattachments
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_mailattachments database mail view
ms.assetid: aee87059-a4c1-459a-a95c-641b4e3f0e73
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 36c5433f51191004a994b1afb3486db89a317acb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "33220693"
---
# <a name="sysmailmailattachments-transact-sql"></a>sysmail_mailattachments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールに送信された添付ファイルごとに 1 行のデータを格納します。 データベース メールの添付ファイルに関する情報を確認するには、このビューを使用します。 データベース メールを使用するによって処理されるすべての電子メールを確認する[sysmail_allitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**attachment_id**|**int**|添付ファイルの識別子。|  
|**mailitem_id**|**int**|添付ファイルが含まれていたメール アイテムの識別子。|  
|**filename**|**nvarchar(520)**|添付ファイルのファイル名。 ときに**attach_query_result**は 1 と**query_attachment_filename**が NULL の場合、データベース メールは、任意のファイル名を作成します。|  
|**filesize**|**int**|添付ファイルのサイズ (バイト単位)。|  
|**attachment**|**varbinary(max)**|添付ファイルの内容。|  
|**last_mod_date**|**datetime**|行が最後に変更された日時。|  
|**last_mod_user**|**sysname**|行を最後に変更したユーザー。|  
  
## <a name="remarks"></a>コメント  
 データベース メールのトラブルシューティングでは、このビューを使用して、添付ファイルのプロパティを確認できます。  
  
 添付ファイル、システム テーブルに格納されている可能性があります、 **msdb**データベースを拡張します。 使用して**sysmail_delete_mailitems_sp**メール アイテムとその関連する添付ファイルを削除します。 詳細については、次を参照してください。[アーカイブ データベース メール メッセージおよびイベント ログには、SQL Server エージェント ジョブを作成する](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)です。  
  
## <a name="permissions"></a>アクセス許可  
 与え、 **sysadmin**固定サーバー ロールおよび**DatabaseMailUserRole**データベース ロール。 メンバーによって実行されると、 **sysadmin**固定サーバー ロール、このビューはすべての添付ファイルを表示します。 その他のユーザーの場合は、自分が送信したメッセージの添付ファイルだけを確認できます。  
  
## <a name="see-also"></a>参照  
 [sysmail_allitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_faileditems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [sysmail_sentitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)   
 [sysmail_unsentitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)  
  
  
