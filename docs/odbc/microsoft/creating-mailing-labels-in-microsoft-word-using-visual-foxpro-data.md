---
title: 宛名ラベル Visual FoxPro データを使用して Microsoft Word で作成する |Microsoft ドキュメント
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
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 858379b3aa670a4e6bb8776303e2d16c85c9d30b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899557"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>宛名ラベル Visual FoxPro データを使用して Microsoft Word で作成します。
Visual FoxPro データは、Windows 95 または Windows 98 のドキュメントの Microsoft Word で使用できます。 たとえば、Visual FoxPro テーブルに格納されている顧客の情報から宛名ラベルを作成することができます。  
  
### <a name="to-create-mailing-labels"></a>絞り込みメール配信のラベルを作成するには  
  
1.  Microsoft Word では、新しい空白の図面を作成します。  
  
2.  [ツール] メニューには、文書の差し込みを選択します。  
  
3.  文書の差し込みヘルパーでは、Create を選択し、宛名ラベルを選択します。  
  
4.  メイン ドキュメントでは、アクティブなウィンドウを選択します。  
  
5.  データ ソース、データの取得を選択してからデータ ソースを開く。  
  
6.  データ ソースを開く ダイアログ ボックスで、MS クエリを選択します。  
  
7.  データ ソースの選択 ダイアログ ボックスで、Visual FoxPro データ ソースを選択し、使用 をクリックします。  
  
8.  データ ソースからアクセスされるデータベースには、テーブルが含まれている場合は、テーブルの追加 ダイアログ ボックスからテーブルを選択します。 Microsoft のクエリでは、クエリ デザイナーの上部に追加されたテーブルが表示されます。  
  
9. ドラッグして、テーブルの下半分デザイナーのクエリのフィールドを選択します。  
  
10. [ファイル] メニューから Microsoft Word へ返されるデータを選択します。 Microsoft クエリが終了し、選択したデータは、文書の差し込みドキュメントで使用可能です。  
  
11. メイン ドキュメントでは、セットアップを選択します。  
  
12. ラベルのオプション ダイアログ ボックスで、ok をクリックしてプリンターとラベル情報を選択します。  
  
13. ラベルの作成 ダイアログ ボックスで、宛名ラベルに印刷し、ok をクリックするフィールドを選択します。  
  
14. 文書の差し込みヘルパーのドキュメントをデータのマージ マージをクリックします。  
  
15. マージ ダイアログ ボックスでは、マージ をクリックしてオプションを選択します。
