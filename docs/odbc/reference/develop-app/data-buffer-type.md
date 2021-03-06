---
title: データ バッファーの種類 |Microsoft ドキュメント
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
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d270c7e2bdd525a585c31a5c29c6b784fa8d1105
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910478"
---
# <a name="data-buffer-type"></a>データ バッファーの種類
バッファーの C データ型は、アプリケーションで指定します。 1 つの変数では、アプリケーションにより、変数を割り当てるとこれに発生します。 汎用的なメモリと、メモリが void 型のポインターが指すは、— このアプリケーションは、特定の種類にメモリをキャストする場合に発生します。 ドライバーには、この型には 2 つの方法が検出されます。  
  
-   **データ バッファーの型引数です。** バッファーが使用してバインドなどのパラメーター値と、結果セットのデータを転送するために使用するバッファー *TargetValuePtr*で**SQLBindCol**、通常、関連付けられている型引数を指定しなければ、ように、 *TargetType*引数**SQLBindCol**です。 この引数では、アプリケーションは、バッファーの種類に対応する C 型識別子を渡します。 たとえば、呼び出しでは、次に**SQLBindCol**、SQL_C_TYPE_DATE 値ドライバーに指示する、*日付*バッファーが、SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     型識別子の詳細については、次を参照してください。、 [ODBC でのデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md) セクションで、このセクションで後述します。  
  
-   **定義済みの型。** 送信およびオプションや、バッファーなどの属性を取得するために使用するバッファーを指す、 *InfoValuePtr*引数**SQLGetInfo**、指定されたオプションに依存する型は固定であります。 ドライバーは、この型のデータ バッファーを前提としています。この種類のバッファーを割り当て、アプリケーションの責任です。 たとえば、呼び出しでは、次に**SQLGetInfo**ドライバーでは、バッファーが SQL_STRING_FUNCTIONS オプションが必要なので、32 ビット整数が前提としています。  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 ドライバーは、バッファー内のデータを解釈するのに C データ型を使用します。
