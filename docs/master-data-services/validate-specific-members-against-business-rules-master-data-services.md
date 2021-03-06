---
title: ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 37bf689ff457cda1717609b293661a7f4344dbc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールに対してメンバーのサブセットを更新または検証する場合にビジネス ルールを選択的に適用します。  
  
> [!NOTE]  
>  ビジネス ルールをモデルのバージョンのすべてのメンバーに適用する場合は、「 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)」を参照してください。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   ビジネス ルールを適用するモデル オブジェクトに対して、 **更新** 権限が最低限必要です。  
  
### <a name="to-apply-business-rules-selectively"></a>ビジネス ルールを選択的に適用するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ドロップダウン リストからモデルを選択します。  
  
2.  **[バージョン]** ドロップダウン リストからバージョンを選択します。  
  
3.  **[エクスプローラー]** タブをクリックします。  
  
4.  メニュー バーの **[エンティティ]** をポイントして、ルールを適用するメンバーを含むエンティティの名前をクリックします。  
  
5.  **[ルールの適用]** をクリックします。 ビジネス ルールは、グリッドに表示されているメンバーにのみ適用されます。  
  
## <a name="see-also"></a>参照  
 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  
