---
title: '[テーブルの追加] ダイアログ ボックス (クエリ デザイナーおよびビュー デザイナー) (Visual DB tools) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 809905693c69802a2aa82f4ab6a9fe0177c43c38
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33047299"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>[テーブルの追加] ダイアログ ボックス (クエリ デザイナーおよびビュー デザイナー) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このダイアログ ボックスを使用すると、クエリまたはビューに、テーブル、ビュー、ユーザー定義関数、またはシノニムを追加できます。  
  
> [!NOTE]  
> テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。  
  
## <a name="options"></a>および  
**テーブル**  
**[ダイアグラム]** ペインに追加できるテーブルを一覧表示します。 テーブルを追加するには、テーブルを選択して **[追加]** をクリックします。 複数のテーブルを一度に追加するには、それらのテーブルを選択して **[追加]** をクリックします。  
  
**ビュー**  
**[ダイアグラム]** ペインに追加できるビューを一覧表示します。 ビューを追加するには、ビューを選択して **[追加]** をクリックします。 複数のビューを一度に追加するには、それらのビューを選択して **[追加]** をクリックします。  
  
**関数**  
**[ダイアグラム]** ペインに追加できるユーザー定義関数を一覧表示します。 関数を追加するには、関数を選択して **[追加]** をクリックします。 複数の関数を一度に追加するには、それらの関数を選択して **[追加]** をクリックします。  
  
**シノニム**  
**[ダイアグラム]** ペインに追加できるシノニムを一覧表示します。 シノニムを追加するには、シノニムを選択して **[追加]** をクリックします。 複数のシノニムを一度に追加するには、それらのシノニムを選択して **[追加]** をクリックします。  
  
**[更新]**  
一覧を更新します。最後の一覧取得以降にデータベースに対して行われた変更が掲載されます。  
  
**[追加]**  
選択した項目を追加します。  
  
## <a name="see-also"></a>参照  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
