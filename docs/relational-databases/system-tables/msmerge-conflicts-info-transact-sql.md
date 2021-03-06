---
title: MSmerge_conflicts_info (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d5990e8dc08545597e18832e6f6b44bfbfce6514
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33006669"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflicts_info**テーブルは、マージ パブリケーションに対するサブスクリプションを同期するときに発生する競合を追跡します。 競合を優先されなかった行のデータが格納されている、 [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md)テーブル アーティクルの競合が発生しました。 このテーブルは、パブリッシャー側ではパブリケーション データベースに、サブスクライバー側ではサブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネーム。|  
|**rowguid**|**uniqueidentifier**|競合している行の識別子です。|  
|**origin_datasource**|**nvarchar (255)**|競合している変更が発生したデータベースの名前です。|  
|**conflict_type**|**int**|発生した競合の種類です。次のいずれかの値をとります。<br /><br /> **1** = 更新の競合: 行レベルで競合が検出されました。<br /><br /> **2** = 列更新の競合: 列レベルで検出された競合します。<br /><br /> **3** = 更新削除 Wins の競合: 削除競合で優先されます。<br /><br /> **4** = 更新 Wins の削除の競合: 競合を避けるに削除された rowguid がこのテーブルに記録されます。<br /><br /> **5** = 挿入のアップロードの失敗: サブスクライバーからの挿入がパブリッシャーで適用できませんでした。<br /><br /> **6** = 挿入のダウンロードに失敗: サブスクライバーでパブリッシャーからの挿入を適用できませんでした。<br /><br /> **7** = アップロード削除に失敗: サブスクライバーでの削除がパブリッシャーにアップロードできませんでした。<br /><br /> **8** = 削除のダウンロードに失敗: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = アップロード更新失敗: パブリッシャー、サブスクライバーでの更新を適用できませんでした。<br /><br /> **10** = 更新のダウンロードに失敗: パブリッシャーでの更新がサブスクライバーに適用できませんでした。<br /><br /> **11**解像度を =<br /><br /> **12** = 論理レコードの更新が優先 Delete: 削除された論理レコード競合を避けるはこのテーブルに記録されます。<br /><br /> **13** = 論理レコード競合挿入を更新します。 論理レコードを挿入、更新プログラムに競合しています。<br /><br /> **14** = 論理レコードの削除が優先更新の競合: 競合を避ける更新された論理レコードはこのテーブルに記録されます。|  
|**reason_code**|**int**|状況依存エラー コード。 この列で使用される値では更新-更新と更新と削除の競合の場合は、同じ、 **conflict_type**です。 ただし、変更の失敗による競合の場合は、マージ エージェントが変更を適用できなかったことを示すエラーが理由コードとなります。 たとえば場合は、マージ エージェントは、主キー違反のため、サブスクライバーの挿入を適用することはできません、ログに記録、 **conflict_type** 6 (「挿入のダウンロードに失敗しました」) の**reason_code** 2672 が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]主キー違反の内部エラー メッセージ:"%ls 制約の違反 ' %. * %1! です。 オブジェクトに重複するキーを挿入できません ' % です。\*%ls"。|  
|**reason_text**|**nvarchar(720)**|状況依存エラーの説明。|  
|**pubid**|**uniqueidentifier**|パブリケーションの識別子です。|  
|**MSrepl_create_time**|**datetime**|競合が発生した時刻です。|  
|**origin_datasource_id**|**uniqueidentifier**|競合している変更が発生したデータベースの識別子です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
