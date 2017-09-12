---
title: "日 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98e0a1f548fdec917f265595a4a06ec795c5f37e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定した日付 (月の日) を表す整数を返します*日付*です。
  
すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DAY ( date )  
```  
  
## <a name="arguments"></a>引数  
*date*  
式に解決されることができるは、**時間**、**日付**、 **smalldatetime**、 **datetime**、 **datetime2**、または**datetimeoffset**値。 *日付*引数は、式、列式、ユーザー定義変数またはリテラル文字列を指定できます。
  
## <a name="return-type"></a>戻り値の型  
**int**
  
## <a name="return-value"></a>戻り値  
1 日と同じ値を返します[DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**日**、*日付*)。
  
場合*日付*は 1、基本の日の時刻の部分では、戻り値だけが含まれています。
  
## <a name="examples"></a>使用例  
次のステートメントから`30`です。 これは、日を表す値です。
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
次のステートメントから`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
次の例を返します`30`です。 これは、日を表す値です。
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP 1 DAY('2010-07-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
次の例を返します`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


