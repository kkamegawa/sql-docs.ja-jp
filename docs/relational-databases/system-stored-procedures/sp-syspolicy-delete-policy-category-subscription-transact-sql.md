---
title: sp_syspolicy_delete_policy_category_subscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_category_subscription_TSQL
- sp_syspolicy_delete_policy_category_subscription
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_category_subscription
ms.assetid: eeab0120-c869-4c95-a79d-6dc418d0b23a
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb514ae527e7b3a116dfa96974e1b8342a953363
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261458"
---
# <a name="spsyspolicydeletepolicycategorysubscription-transact-sql"></a>sp_syspolicy_delete_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のデータベースのポリシー カテゴリのサブスクリプションを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_delete_policy_category_subscription [ @policy_category_subscription_id = ] policy_category_subscription_id  
```  
  
## <a name="arguments"></a>引数  
 [  **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 ポリシー カテゴリのサブスクリプションの識別子を指定します。 *policy_category_subscription_id*は**int**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syspolicy_delete_policy_category_subscription は msdb システム データベースのコンテキストで実行する必要があります。  
  
 サブスクリプションが必須の場合は、ポリシー カテゴリのサブスクリプションを削除できません。  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャは、ストアド プロシージャの現在の所有者のコンテキストで実行されます。  
  
 値を取得する*policy_category_subscription_id*、次のクエリを使用することができます。  
  
```  
SELECT a.policy_category_subscription_id, a.target_object, b.name AS category_name  
FROM msdb.dbo.syspolicy_policy_category_subscriptions AS a  
INNER JOIN msdb.dbo.syspolicy_policy_categories AS b  
ON a.policy_category_id = b.policy_category_id;  
```  
  
## <a name="examples"></a>使用例  
 次の例では、ID が 1 であるポリシー カテゴリのサブスクリプションを削除します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_category_subscription @policy_category_subscription_id = 1;  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)  
  
  
