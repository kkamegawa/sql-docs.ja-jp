---
title: SQLRemoveDefaultDataSource 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 072f599ad63e7b624478e66030356367d944fd17
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916617"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource 関数
**準拠**  
 バージョンが導入されています。 ODBC 1.0 では、非推奨  
  
 **概要**  
 ODBC 3.0 では、 **SQLRemoveDefaultDataSource**関数が呼び出しによって置き換えられました[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)で、*起こり*ODBC_REMOVE_DEFAULT_DSN の引数。 場合、ODBC 2 *.x*インストール プログラムは、この関数を呼び出し、ODBC のインストーラーを使用すると、次にマップする**SQLConfigDataSource**呼び出し。  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
