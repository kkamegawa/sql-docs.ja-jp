---
title: データ型 (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0e703c80db732560a45db72d8f8c0bf2a2ce21fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32938347"
---
# <a name="data-types-extended-stored-procedure-api"></a>データ型 (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 拡張ストアド プロシージャ API のデータ型を使用するには、プログラムに Srv.h ヘッダー ファイルをインクルードします。  
  
|データ型|SQL Server データ型|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|**[バイナリ]**|**binary** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGCHAR|**char**|**character** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGVARBINARY|**varbinary**|可変長 **binary** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBIGVARCHAR|**varchar**|可変長 **character** データ型。長さは 0 から 8,000 バイトです。|  
|SRVBINARY|**[バイナリ]**|**binary** データ型。|  
|SRVBIT|**Bit**|**bit** データ型。|  
|SRVBITN|**bit null**|**bit** データ型。NULL 値を許容します。|  
|SRVCHAR|**char**|**character** データ型。|  
|SRVDATETIME|**datetime**|8 バイトの **datetime** データ型。|  
|SRVDATETIM4|**smalldatetime**|4 バイトの **smalldatetime** データ型。|  
|SRVDATETIMN|**datetime null**|**smalldatetime** または **datetime** データ型。NULL 値を許容します。|  
|SRVDECIMAL|**decimal**|**decimal** データ型。|  
|SRVDECIMALN|**decimal null**|**decimal** データ型。NULL 値を許容します。|  
|SRVFLT4|**real**|4 バイトの **real** データ型。|  
|SRVFLT8|**float**|8 バイトの **float** データ型。|  
|SRVFLTN|**real** &#124; **float null**|**real** または **float** データ型。NULL 値を許容します。|  
|SRVIMAGE|**image**|**image** データ型。|  
|SRVINT1|**tinyint**|1 バイトの **tinyint** データ型。|  
|SRVINT2|**smallint**|2 バイトの **smallint** データ型。|  
|SRVINT4|**int**|4 バイトの **int** データ型。|  
|SRVINTN|**tinyint** &#124; **smallint** &#124; **int null**|**tinyint**、**smallint**、または **int** データ型。NULL 値を許容します。|  
|SRVMONEY4|**smallmoney**|4 バイトの **smallmoney** データ型。|  
|SRVMONEY|**money**|8 バイトの **money** データ型。|  
|SRVMONEYN|**money** &#124; **smallmoney null**|**smallmoney** または **money** データ型。NULL 値を許容します。|  
|SRVNCHAR|**nchar**|Unicode の **character** データ型。|  
|SRVNTEXT|**ntext**|Unicode の **text** データ型。|  
|SRVNUMERIC|**numeric**|**numeric** データ型。|  
|SRVNUMERICN|**numeric null**|**numeric** データ型。NULL 値を許容します。|  
|SRVNVARCHAR|**nvarchar**|Unicode の可変長の **character** データ型。|  
|SRVTEXT|**text**|**text** データ型。|  
|SRVVARBINARY|**varbinary**|可変長の **binary** データ型。|  
|SRVVARCHAR|**varchar**|可変長の **character** データ型。|  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
