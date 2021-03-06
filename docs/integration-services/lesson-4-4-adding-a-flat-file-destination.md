---
title: '手順 4 : フラット ファイル変換先の追加 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d50777afbba77d87e6988338835f3cec023ee4d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-4-4---adding-a-flat-file-destination"></a>レッスン 4-4 - フラット ファイル変換先の追加
Lookup Currency Key 変換のエラー出力では、参照操作に失敗したデータ行がスクリプト変換にリダイレクトされます。 スクリプト変換ではスクリプトが実行され、発生したエラーに関するさらに詳しい情報を記述したエラーの説明が取得されます。  
  
ここでは、後の処理に向けて、失敗した行に関するすべての情報を区切りファイルに保存します。 失敗した行を保存するには、フラット ファイル接続マネージャーで、フラット ファイル変換先を追加し、エラー データを保存するテキスト ファイルを構成する必要があります。 フラット ファイル変換先が使用するフラット ファイル接続マネージャーでプロパティを設定することにより、フラット ファイル変換先がテキスト ファイルをフォーマットする方法と書き込む方法を指定できます。 詳細については、「 [フラット ファイル接続マネージャー](../integration-services/connection-manager/flat-file-connection-manager.md) 」および「 [フラット ファイル変換先](../integration-services/data-flow/flat-file-destination.md)」を参照してください。  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a>新しいフラット ファイルを追加し、エラー データが読み込まれるように構成するには  
  
1.  **[データ フロー]** タブをクリックします。  
  
2.  **[SSIS ツールボックス]** で **[その他]** を展開し、 **[フラット ファイル変換先]** をデータ フロー デザイン画面上にドラッグします。 **[フラット ファイル変換先]** を **[Get Error Description]** 変換のすぐ下にドロップします。  
  
3.  **[Get Error Description]** 変換をクリックし、緑の矢印を新しい **[フラット ファイル変換先]** までドラッグします。  
  
4.  **[データ フロー]** デザイン画面で、新しく追加した **[フラット ファイル変換先]** 変換の **[フラット ファイル変換先]** をクリックし、名前を **Failed Rows**に変更します。  
  
5.  この **Failed Rows** 変換を右クリックし、 **[編集]** をクリックします。次に、 **[フラット ファイル変換先エディター]** の **[新規作成]** をクリックします。  
  
6.  **[フラット ファイル形式]** ダイアログ ボックスで、 **[区切り記号]** が選択されていることを確認し、 **[OK]** をクリックします。  
  
7.  **[フラット ファイル接続マネージャー エディター]** の **[接続マネージャー名]** ボックスに、「 **Error Data**」と入力します。  
  
8.  **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[参照]** をクリックし、ファイルの保存先のフォルダーに移動します。  
  
9. **[ファイルを開く]** ダイアログ ボックスで、 **[ファイル名]** に「 **ErrorOutput.txt**」と入力し、 **[開く]** をクリックします。  
  
10. **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[ロケール]** ボックスに [英語 (米国)]、 **[コード ページ]** に [1252 (ANSI - ラテン I)] が表示されていることを確認します。  
  
11. [オプション] ペインで、 **[列]** をクリックします。  
  
    変換元データ ファイルの列に加え、新しい 3 つの列 (ErrorCode、ErrorColumn、および ErrorDescription) が表示されます。 これらの列は、Lookup Currency Key 変換のエラー出力と Get Error Description 変換のスクリプトによって生成されたものです。これらの列は、失敗した行の問題を解決するために使用できます。  
  
12. **[OK]** をクリックします。  
  
13. **[フラット ファイル変換先エディター]** で、 **[ファイル内のデータを上書きする]** チェック ボックスをオフにします。  
  
    このチェック ボックスをオフにすると、複数のパッケージ実行でエラーが継続します。  
  
14. **[フラット ファイル変換先エディター]** の **[マッピング]** をクリックし、すべての列が正しいことを確認します。 必要に応じて、変換先の列の名前を変更できます。  
  
15. **[OK]** をクリックします。  
  
## <a name="next-steps"></a>Next Steps  
[手順 5: レッスン 4 のチュートリアル パッケージのテスト](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
  
