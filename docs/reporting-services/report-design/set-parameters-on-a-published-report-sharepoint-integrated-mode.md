---
title: "SharePoint 統合モードのパブリッシュされたレポートのパラメーターを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ba05b4727499c702b9f8827de9564aad444c1ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="set-parameters-on-a-published-report---sharepoint-integrated-mode"></a>SharePoint 統合モードのパブリッシュされたレポートのパラメーターを設定します。
  パラメーター化されたレポートとは、レポートの実行時にデータのフィルター処理に使用する入力値を受け取るレポートです。 パラメーターは、レポートの作成時に定義します。 レポート定義でレポート パラメーターがどのように定義されているかによって、単一の値、複数の値、または動的な値を受け入れることができます。動的な値は、直前の選択に応じて変化します (たとえば、製品カテゴリを選択したとき、次の選択ではそのカテゴリの特定の製品を選択するなど)。 パラメーターには既定値を指定することもできます。フィルター選択したレポートを自動的に実行する場合に既定値を使用することも、既定値を別の値に置き換えることもできます。  
  
 このようなプロパティはレポート定義で設定することも、レポートがパブリッシュされた後で設定することもできます。 パブリッシュされたレポートの一部のパラメーター プロパティを変更して、値や表示プロパティを変更することはできますが、パラメーターの名前やデータ型を変更することはできません。 パラメーター名とデータ型は、レポート作成者のみがレポート定義内で変更できます。  
  
 パラメーター化されたレポートを実行する際、有効な値を示すドロップダウン リストがレポートに含まれており、そこから選択できることもありますが、一般的には入力する値の種類を知っておく必要があります。  
  
 パブリッシュ済みレポートのパラメーター プロパティを設定するには、レポートに対する "アイテムの編集" 権限が必要です。 SharePoint サイトから実行するレポートの、一部またはすべてのパラメーター プロパティを変更できます。 繰り返し使用するパラメーター値の組み合わせを保存することで、レポートを個人用にカスタマイズすることはできません。 指定した既定値は、レポートを開いたすべてのユーザーによって使用されます。  
  
 レポートを常に表示するように構成されたレポート ビューアー Web パーツにレポートを埋め込む場合には、レポート ビューアー Web パーツのプロパティを設定します。 詳細については、「[レポート ビューアー Web パーツを Web ページに追加する &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)」をご覧ください。  
  
### <a name="to-run-a-parameterized-report"></a>パラメーター化されたレポートを実行するには  
  
1.  レポートが格納されているライブラリを開きます。  
  
2.  レポート名をクリックします。 パラメーターのあるレポートをあらかじめ調べておく必要があります。 レポートの外観からは、パラメーター化されているかどうか判別できません。  
  
3.  レポートを開き、使用するパラメーターを指定します。 パラメーター領域は、レポート ビューアー Web パーツのプロパティ設定に応じて、表示、折りたたみ、または非表示になっています。  
  
    1.  パラメーター領域が表示されている場合は、各パラメーターの値を選択します。  
  
    2.  レポートの縦方向に色付きの細い枠が表示され、その中央部に矢印がある場合、パラメーター領域が折りたたまれています。 矢印をクリックすると、展開できます。  
  
    3.  パラメーター領域が非表示になっている場合、値を指定することはできません。  
  
4.  パラメーター領域の下部にある **[適用]** をクリックすると、レポートが実行されます。  
  
     期待する結果を得られない値の組み合わせを指定してしまう可能性もあります。 必要な情報が得られない場合は、作成者によるレポートの変更が必要である可能性があります。  
  
5.  **[OK]**をクリックします。  
  
### <a name="to-set-parameter-properties"></a>パラメーター プロパティを設定するには  
  
1.  レポートが格納されているライブラリまたはフォルダーを開きます。  
  
2.  レポートをポイントして、下向きの矢印をクリックします。  
  
3.  **[パラメーターの管理]**をクリックします。 レポートにパラメーターが含まれている場合、ページに各パラメーターが一覧表示されます。 一覧には、パラメーターの名前、データ型、既定で使用されるデータ値、およびレポートを開いたときにパラメーター領域を表示するかどうかが示されます。  
  
4.  一覧で、設定を変更するパラメーターをクリックします。  
  
5.  [既定値] に、パラメーターの値を入力します。 この値は検証されないため、レポートに対して有効な値を入力するように注意してください。  
  
    1.  レポートの作成時に定義された既定値を使用するには、 **[レポート定義で指定されている値式を使用]** を選択します。 レポート定義で既定値が指定されていない場合、このオプションは使用できません。  
  
    2.  レポート定義の既定値を置き換える値を指定するには、 **[レポートの既定値を上書き]** を選択します。 NULL 値が許可されるレポート パラメーターについては、 **[Null]** チェック ボックスをオンにすることで、そのパラメーターに基づくフィルター処理を無効にすることができます。  
  
    3.  レポートが処理される前に各ユーザーが値を指定できるようにするには、 **[パラメーターは既定値を持たない]** を選択します。 このオプションを選択した場合、ユーザーに値の指定を求めるための表示設定を行う必要があります。  
  
     すべてのパラメーターに既定値があれば、ユーザーがレポートを開くと自動的にその既定値を使用してレポートが実行されます。 ただし、レポート領域が表示される場合には、ユーザーは既定値を変更してレポートを再実行することができます。  
  
6.  パラメーターを表示するかどうかを決定する表示オプションを設定します。  
  
    1.  ページにパラメーターを表示するには、 **[ユーザーにメッセージを表示]** を選択します。 フィールド内に表示される入力要求テキストで、ユーザーが入力する必要のあるデータの形式や型に関する簡単な説明を示すことができます。  
  
    2.  既定値を使用し、パラメーター領域にパラメーターを表示しない場合には、 **[非表示]** を選択します。  
  
    3.  既定値を使用し、パラメーター領域にもサブスクリプション ページにもパラメーターを表示しない場合には、 **[内部]** を選択します。  
  
7.  **[適用]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  