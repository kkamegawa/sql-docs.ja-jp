---
title: FILESTREAM DDL、関数、ストアド プロシージャ、およびビュー | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: blob
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d95d8ba2986c4e426f8035bec003884114393496
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918197"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a>FILESTREAM DDL、関数、ストアド プロシージャ、およびビュー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  FILESTREAM をサポートする Transact-SQL ステートメントおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトの一覧を示します。  
  
 FileTable 機能をサポートするデータベース オブジェクトの一覧については、「 [FileTable DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)」を参照してください。  
  
##  <a name="ddl"></a> Transact-SQL データ定義言語 (DDL) ステートメント  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)DROP INDEX  
  
##  <a name="func"></a> システム関数  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/get-filestream-transaction-context-transact-sql.md)  
  
-   [PathName &#40;Transact-SQL&#41;](../../relational-databases/system-functions/pathname-transact-sql.md)  
  
##  <a name="proc"></a> システム ストアド プロシージャ  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
-   [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
##  <a name="cat"></a> システム ビュー: カタログ ビュー  
  
-   [sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
  
##  <a name="dmv"></a> システム ビュー: 動的管理ビュー  
  
-   [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
  
-   [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
  
##  <a name="api"></a> プログラミング API  
  
-   [OpenSqlFilestream による FILESTREAM データへのアクセス](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
-   [マネージ API: SqlFileStream クラス](http://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
