---
title: カーソル ライブラリのキャッシュ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 003b9497177aa0bf2da1c58ad01644ea014b5b14
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906907"
---
# <a name="cursor-library-cache"></a>カーソル ライブラリのキャッシュ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 結果セット内のデータの各行は、カーソル ライブラリは、各列のデータ バインド、バインドされた各列のデータの長さと、行の状態をキャッシュします。 カーソル ライブラリでは、両方のキャッシュ内で値を使用して経由**SQLFetch**と**SQLFetchScroll**と位置指定操作の検索結果のステートメントを作成します。 詳細については、次を参照してください。[検索ステートメントを構築する](../../../odbc/reference/appendixes/constructing-searched-statements.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [列のデータ](../../../odbc/reference/appendixes/column-data.md)  
  
-   [列データの長さ](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [行の状態](../../../odbc/reference/appendixes/row-status.md)  
  
-   [キャッシュの場所](../../../odbc/reference/appendixes/location-of-cache.md)
