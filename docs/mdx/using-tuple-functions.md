---
title: 組関数の使用 |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 578192fa982b8bbf65527f4ff1d71b6595a2400d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743827"
---
# <a name="using-tuple-functions"></a>組関数の使用


  組関数は、組をセットから取得します。または、組の文字列表記を解決することによって組を取得します。  
  
 組関数は、メンバー関数や集合関数と同様に、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用される多次元構造を操作するために不可欠です。  
  
 MDX では、次の 3 つの組関数がある[Current&#40;MDX&#41;](../mdx/current-mdx.md)、[Item&#40;組&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)と[StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md). 次のクエリの例では、各組関数の使用方法を示します。  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [Functions&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)   
 [メンバー関数の使用](../mdx/using-member-functions.md)   
 [集合関数の使用](../mdx/using-set-functions.md)  
  
  
