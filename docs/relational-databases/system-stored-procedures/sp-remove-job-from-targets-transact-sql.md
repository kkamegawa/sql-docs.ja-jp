---
title: sp_remove_job_from_targets (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b74ba0fee691ba80ac62181b108c8d1047479817
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255042"
---
# <a name="spremovejobfromtargets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したジョブを指定した対象サーバーまたは対象サーバー グループから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id =**] *job_id*  
 指定された対象サーバーまたは対象サーバー グループから削除されるジョブのジョブ識別番号を指定します。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name =**] **'***job_name***'**  
 指定された対象サーバーまたは対象サーバー グループから削除されるジョブの名前を指定します。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。 *job_name*は**sysname**、既定値は NULL です。  
  
 [ **@target_server_groups =**] **'***target_server_groups***'**  
 指定したジョブの削除元である対象サーバー グループをコンマで区切って指定します。 *target_server_groups*は**nvarchar (1024)**、既定値は NULL です。  
  
 [ **@target_servers =**] **'***target_servers***'**  
 指定したジョブの削除元である対象サーバーをコンマで区切って指定します。 *target_servers*は**nvarchar (1024)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>権限  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、削除前に作成した`Weekly Sales Backups`からジョブ、`Servers Processing Customer Orders`対象サーバー グループとの間、`SEATTLE1`と`SEATTLE2`サーバー。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_apply_job_to_targets &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
