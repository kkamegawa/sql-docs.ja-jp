---
title: テンプレートを使用したリソース ガバナーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1d1299a1e646c2297ef2dc0e5979a42f9a5ebf6b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="configure-resource-governor-using-a-template"></a>テンプレートを使用してリソース ガバナーを構成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に用意されているテンプレートを使用してリソース ガバナーを構成できます。  
  
-   **Before you begin:**  [Permissions](#Permissions)  
  
-   **ワークロード グループの作成に使用するもの:**  [テンプレート](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 次の手順に従って、リソース プールおよびそのプールのワークロード グループを作成するテンプレートを開いて変更します。 また、このテンプレートを使用すると、既定のグループまたは作成したワークロード グループへの新しい接続をルーティングするための、ユーザー定義の分類子関数を作成できます。  
  
###  <a name="Permissions"></a> Permissions  
 テンプレートでリソース ガバナーの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="ConfRGTemplate"></a> テンプレートを使用してリソース ガバナーを構成する  
 **のテンプレートを使用してリソース ガバナーを構成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  **テンプレート エクスプローラー**で、 **[リソース ガバナー]** を展開して、 **[リソース ガバナーの構成]** をダブルクリックします。  
  
3.  **[データベース エンジンへの接続]** で、必要な情報を入力し、 **[OK]** をクリックします。 テンプレート Configure Resource Governor.sql がクエリ エディターに示されます。 このテンプレートを使用して、リソース プール、ワークロード グループ、および分類子関数を構成します。  
  
4.  テンプレートの値を変更するには、Ctrl キーと Shift キーを押しながら M キーを押します。 **[テンプレート パラメーターの値の指定]** ウィンドウで、使用する値を入力します。  
  
5.  テンプレートに加えた変更を保存するには、 **[OK]** をクリックします。  
  
6.  クエリを実行するには、 **[実行]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [リソース ガバナーの有効化](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [リソース ガバナー ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [リソース ガバナーの分類子関数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [リソース ガバナー プロパティの表示](../../relational-databases/resource-governor/view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
