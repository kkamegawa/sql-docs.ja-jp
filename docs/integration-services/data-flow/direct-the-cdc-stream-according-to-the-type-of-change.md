---
title: 変更の種類に応じた CDC ストリームのダイレクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 873d517e84844d83db908473d3e20fe6e78bc2b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>変更の種類に応じた CDC ストリームのダイレクト
  CDC スプリッター変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの CDC ソースが含まれている必要があります。  
  
 パッケージに追加する CDC ソースでは、NetCDC 処理モードが選択されている必要があります。 処理モードの選択の詳細については、[「CDC ソース エディター ([接続マネージャー] ページ)」](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md) を参照してください。  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>変更の種類に応じて CDC ストリームをダイレクトするには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、CDC スプリッターをデザイン画面にドラッグします。  
  
4.  パッケージに含まれている CDC ソースを CDC スプリッターに接続します。  
  
5.  CDC スプリッターを、1 つまたは複数の変換先に接続します。 最大 3 つの出力に接続することができます。  
  
6.  以下の出力のいずれかを選択します。  
  
    -   削除出力: DELETE 変更行のダイレクト先の出力。  
  
    -   挿入出力: INSERT 変更行のダイレクト先の出力。  
  
    -   更新出力: 更新前および更新後の UPDATE 変更行と、Merge 変更行のダイレクト先の出力。  
  
7.  必要に応じて、 **[詳細エディター]** ダイアログ ボックスを使用して、詳細なプロパティを構成できます。  
  
     **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。  
  
     **[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。  
  
    -   **プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、CDC スプリッターを右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
     CDC スプリッターの使用方法の詳細については、「Microsoft SQL Server Integration Services の CDC コンポーネント」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC スプリッター](../../integration-services/data-flow/cdc-splitter.md)  
  
  
