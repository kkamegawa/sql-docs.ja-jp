---
title: ERROR_LINE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_LINE
- ERROR_LINE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], line number
- TRY...CATCH [SQL Server]
- line number of error [SQL Server]
- ERROR_LINE function
- CATCH block
ms.assetid: 47335734-0baf-45a6-8b3b-6c4fd80d2cb8
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 44745c0f27527872abd1b63c3fa5b3954328c1be
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="errorline-transact-sql"></a>ERROR_LINE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  TRY...CATCH 構造の CATCH ブロックの実行を引き起こすエラーが発生した行番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ERROR_LINE ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロックで呼び出されると、次の値を返します。  
  
-   -エラーが発生した行番号を返します。  
  
-   ストアド プロシージャまたはトリガー内でエラーが発生した場合には、ルーチン内の行番号  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>Remarks  
 この関数は、CATCH ブロックのスコープ内の任意の場所で呼び出すことができます。  
  
 ERROR_LINE は、呼び出された回数や CATCH ブロックのスコープ内のどこで呼び出されたかにかかわらず、エラーが発生した行番号を返します。 これは、エラーが発生したステートメントの直後のステートメントまたは CATCH ブロックの最初のステートメントでエラー番号を返す、@@ERROR などの関数とは異なります。  
  
 入れ子になった CATCH ブロックでは、ERROR_LINE は、参照されている CATCH ブロックのスコープに固有のエラー行番号を返します。 たとえば、TRY...CATCH 構造の CATCH ブロックに、入れ子になった TRY...CATCH 構造が含まれる場合があります。 入れ子になった CATCH ブロック内では、ERROR_LINE は、入れ子になった CATCH ブロックを呼び出したエラーの行番号を返します。 ERROR_LINE が外部の CATCH ブロックで実行されると、その CATCH ブロックを呼び出したエラーの行番号が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errorline-in-a-catch-block"></a>A. CATCH ブロックで ERROR_LINE を使用する  
 次の例では、0 除算エラーを生成する `SELECT` ステートメントを示します。 エラーが発生した行番号が返されます。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorline-in-a-catch-block-with-a-stored-procedure"></a>B. ストアド プロシージャ内の CATCH ブロックで ERROR_LINE を使用する  
 次のコード例では、0 除算エラーを生成するストアド プロシージャを示します。 `ERROR_LINE` は、エラーが発生したストアド プロシージャの行番号を返します。  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
  
### <a name="c-using-errorline-in-a-catch-block-with-other-error-handling-tools"></a>C. CATCH ブロックで ERROR_LINE を他のエラー処理ツールと一緒に使用する  
 次の例では、0 除算エラーを生成する `SELECT` ステートメントを示します。 エラーが発生した行番号と共に、エラーに関する情報が返されます。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  
