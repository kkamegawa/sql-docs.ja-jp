---
title: "xp_grantlogin (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_grantlogin
- xp_grantlogin_TSQL
dev_langs: TSQL
helpviewer_keywords: xp_grantlogin
ms.assetid: c851c1ab-3b29-4b99-9902-78c2665a844b
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eb35af7a2de8fae7d227ea146d2578a73e5c6c28
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="xpgrantlogin-transact-sql"></a>xp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows グループまたはユーザーへのアクセスを付与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_grantlogin {[@loginame = ] 'login'} [,[@logintype = ] 'logintype']  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame =** ] **'***ログイン***'**  
 追加する Windows ユーザーまたはグループの名前を指定します。 Windows ユーザーまたはグループをフォームでの Windows ドメイン名で修飾する必要があります*ドメイン*\\*ユーザー*です。 *ログイン*は**sysname**、既定値はありません。  
  
 [  **@logintype =** ] **'***logintype***'**  
 アクセス権が与えられるログインのセキュリティ レベルを指定します。 *logintype*は**varchar (5)**、既定値は NULL です。 のみ**admin**を指定できます。 場合**admin**が指定されている*ログイン*へのアクセス権が付与[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のメンバーとして追加して、 **sysadmin**固定サーバー ロール。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **xp_grantlogin**はシステム ストアド プロシージャ、拡張ストアド プロシージャではなくなります。 **xp_grantlogin**呼び出し**sp_grantlogin**と**sp_addsrvrolemember**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **securityadmin**固定サーバー ロール。 変更するときに、 *logintype*、メンバーシップが必要、 **sysadmin**固定サーバー ロール。  
  
## <a name="see-also"></a>参照  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_enumgroups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-enumgroups-transact-sql.md)   
 [xp_loginconfig &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)   
 [sp_revokelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)  
  
  