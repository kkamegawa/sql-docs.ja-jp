---
title: 集計関数を使用して |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4e30b5670e7a9a02fdfa9f3bbfad6889e83b562
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026039"
---
# <a name="use-aggregate-functions"></a>集計関数の使用
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  メジャーをスライスするためにディメンションを使用する場合、メジャーはそのディメンションに含まれる階層に沿って集約されます。 この集約動作は、メジャーに指定される集計関数に依存します。 数値データが含まれているほとんどのメジャーでは、集計関数は **Sum**になります。 メジャーの値は、どの階層のレベルがアクティブかに応じて異なる量の合計になります。  
  
 Analysis Services において作成するすべてのメジャーは、対応する集計関数によりその動作が決まります。 定義済みの集計の種類には、**Sum****Min****Max****Count****Distinct Count**、およびその他複数の特化した関数があります。 または、複雑な数式やカスタムの数式に基づいて集計を必要とする場合は、構築済みの集計関数を代わりに使用して、MDX の計算を作成できます。 たとえば、割合の値のためのメジャーを定義する場合、計算されるメジャーを使用して MDX でそれを実行します。 「[CREATE MEMBER ステートメント &#40;MDX&#41;](../../mdx/mdx-data-definition-create-member.md)」を参照してください。  
  
 キューブ ウィザードを使用して作成されるメジャーは、メジャーの定義の一部として、集計の種類に割り当てられます。 ソース列に数値データが含まれることを前提として、集計の種類は常に **Sum**になります。 **Sum** は、ソース列のデータ型に関係なく割り当てられます。 たとえば、キューブ ウィザードを使用してメジャーを作成し、ファクト テーブルからすべての列を抜粋した場合、ソースが日付と時間の列であっても、結果として得られるメジャーのすべてに **Sum**の集計があることが分かります。 集計関数が適切であることを確認するウィザードを介して作成されたメジャーの場合は、事前に割り当てられている集計メソッドを常に確認します。  
  
 [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] または MDX のいずれかを介したキューブの定義で、集計方法を割り当てたり、変更したりすることができます。 詳細については、「[多次元モデル内のメジャーおよびメジャー グループの作成](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)」または「[Aggregate &#40;MDX&#41;](../../mdx/aggregate-mdx.md)」を参照してください。  
  
##  <a name="AggFunction"></a> 集計関数  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、メジャー グループに含まれるディメンションに従ってメジャーを集計するための関数があります。 集計関数の " *加法性* " によって、キューブのすべてのディメンションにわたってメジャーがどのように集計されるかが決まります。 集計関数の加法性は、3 つのレベルに分類されます。  
  
 加法  
 加法メジャーは完全加法メジャーとも呼ばれ、メジャーが含まれているメジャー グループ内のすべてのディメンションに従って制限なく集計できます。  
  
 準加法  
 準加法メジャーは、メジャーが含まれているメジャー グループ内のすべてではなく一部のディメンションに従って集計できます。 たとえば、在庫の数量を表すメジャーは、地理ディメンションに従って集計してすべての倉庫の合計在庫数量を生成できますが、このメジャーは在庫数量の定期的なスナップショットを表しているため、時間ディメンションに従って集計できません。 そのようなメジャーを時間ディメンションに従って集計すると、間違った結果が生成されます。 詳細については、「 [準加法の動作の定義](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md) 」を参照してください。  
  
 非加法  
 非加法メジャーは、メジャーが含まれているメジャー グループ内のどのディメンションに従っても集計できません。 代わりに、このメジャーは、メジャーを表すキューブのセルごとに計算する必要があります。 たとえば、利益率などの比率を返す計算されるメジャーは、どのディメンションの子メンバーのパーセンテージ値からも集計できません。  
  
 次の表は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の集計関数を示しています。関数の加法性と予想される出力が記載されています。  
  
|集計関数|加法性|戻り値|  
|--------------------------|----------------|--------------------|  
|**Sum**|加法|すべての子メンバーの値の合計を計算します。 これは既定の集計関数です。|  
|**Count**|加法|すべての子メンバーの数を取得します。|  
|**Min**|準加法|すべての子メンバーの最低値を取得します。|  
|**Max**|準加法|すべての子メンバーの最高値を取得します。|  
|**DistinctCount**|非加法|すべての一意の子メンバーの数を取得します。 詳細については、次のセクションの「 [個別のカウント メジャーの概要](../../analysis-services/multidimensional-models/use-aggregate-functions.md#bkmk_distinct) 」を参照してください。|  
|**なし**|非加法|集計は行われず、ディメンションのリーフ メンバーおよび非リーフ メンバーのすべての値が、メジャーが含まれているメジャー グループのファクト テーブルから直接入力されます。 ファクト テーブルからメンバーの値を読み取ることができない場合は、そのメンバーの値は Null に設定されます。|  
|**[ByAccount]**|準加法|勘定科目ディメンションのメンバーの勘定科目の種類に割り当てられている集計関数に従って集計します。 勘定科目ディメンションがメジャー グループに存在しない場合は、 **None** 集計関数として扱われます。<br /><br /> 勘定科目ディメンションの詳細については、「 [親子型ディメンションの財務アカウントの作成](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)」を参照してください。|  
|**AverageOfChildren**|準加法|空ではないすべての子メンバーの値の平均を計算します。|  
|**FirstChild**|準加法|最初の子メンバーの値を取得します。|  
|**LastChild**|準加法|最後の子メンバーの値を取得します。|  
|**FirstNonEmpty**|準加法|空ではない最初の子メンバーの値を取得します。|  
|**LastNonEmpty**|準加法|空ではない最後の子メンバーの値を取得します。|  
  
##  <a name="bkmk_distinct"></a> 個別のカウント メジャーの概要  
 **Aggregate Function** プロパティの値が **Distinct Count** であるメジャーは、"個別のカウント メジャー" と呼ばれます。 個別のカウント メジャーを使用すると、ファクト テーブルにおけるディメンションの最下位レベル メンバーの出現数をカウントできます。 カウントは重複しないため、メンバーが複数回発生した場合も 1 つとしてカウントされます。 個別のカウント メジャーは、常に専用のメジャー グループに配置されています。 独自のメジャー グループに個別のカウント メジャーを配置することは、パフォーマンスの最適化の手法としてデザイナーに構築されたベスト プラクティスです。  
  
 個別のカウント メジャーを使用するのは、あるディメンションの各メンバーについて、別のディメンションの重複しない最下位レベルのメンバーが、ファクト テーブル内で行をいくつ共有しているかを調べる場合です。 たとえば、Sales キューブの場合、顧客および顧客グループごとに、何種類の製品が購入されたかを調べます。 つまり、Customers ディメンションの各メンバーに対して、Products ディメンションの重複しない最下位レベル メンバーがファクト テーブル内でいくつの行を共有しているかを調べます。または、Internet Site Visits キューブの場合、サイト閲覧者や閲覧者グループごとに、インターネット サイト上で閲覧された重複しないページ数を調べる場合もあります。 つまり、Site Visitors ディメンションのメンバーごとに、Page ディメンションの重複しない最下位レベルのメンバーがファクト テーブル内の行をいくつ共有しているかを調べます。これらの各サンプルでは、2 番目のディメンションの最下位レベル メンバーが個別のカウント メジャーによってカウントされます。  
  
 このような分析では、ディメンションを 2 つに制限する必要はありません。 実際、カウント対象となるメンバーを含んでいるディメンションなど、キューブ内のディメンションを自由に組み合わせることによって個別のカウント メジャーを分割およびスライスできます。  
  
 メンバーをカウントする個別のカウント メジャーは、ファクト テーブル内の外部キー列に基づきます  (つまり、メジャーの **Source Column** プロパティでこの列を識別します)。この列は、個別のカウント メジャーによってカウントされたメンバーを識別するディメンション テーブル列と結合します。  
  
## <a name="see-also"></a>参照  
 [メジャーとメジャー グループ](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../../mdx/mdx-function-reference-mdx.md)   
 [準加法の動作を定義します。](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md)  
  
  
