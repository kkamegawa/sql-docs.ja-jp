---
title: 次のフェッチ位置 |Microsoft ドキュメント
description: 行のフェッチで次のフェッチ位置
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c5870fefce6e4d989235f5ec1d0672e4b77866d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="fetching-rows---next-fetch-position"></a>行のフェッチで次のフェッチ位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver SQL サーバーが保持の追跡の次のフェッチ位置のためをへの呼び出しのシーケンス、 **GetNextRows**メソッド (の方向、または介在する変更がへの呼び出しにスキップせず、 **FindNextRow**、**シーク**、または**RestartPosition**メソッド) をスキップまたは任意の行を繰り返ししないで行セット全体を読み取ります。 次のフェッチ位置が変更されたかを呼び出して**irowset::getnextrows**、 **irowset::restartposition**、または**irowsetindex::seek**、またはを呼び出すことによって**FindNextRow**と null *pBookmark*値。 呼び出す**FindNextRow** null 以外の値*pBookmark*値では次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  