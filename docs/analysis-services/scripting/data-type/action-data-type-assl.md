---
title: Action データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b717929c61852836527f00809528ccb8d2b26d8d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037273"
---
# <a name="action-data-type-assl"></a>Action データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  内のアクションを表す抽象プリミティブ データ型を定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素または[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Caption>...</Caption>  
      <CaptionIsMdx>...</CaptionIsMdx>  
      <Translations>...</Translations>  
   <TargetType>...</TargetType>  
   <Target>...</Target>  
   <Condition>...</Condition>  
   <Type>...</Type>  
   <Invocation>...</Invocation>  
   <Application>...</Application>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
</Action>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)、 [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)、 [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[アプリケーション](../../../analysis-services/scripting/properties/application-element-assl.md)、[キャプション](../../../analysis-services/scripting/properties/caption-element-assl.md)、 [CaptionIsMdx](../../../analysis-services/scripting/properties/captionismdx-element-assl.md)、[条件](../../../analysis-services/scripting/properties/condition-element-assl.md)、[の説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[呼び出し](../../../analysis-services/scripting/properties/invocation-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[ターゲット](../../../analysis-services/scripting/properties/target-element-assl.md)、 [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[型](../../../analysis-services/scripting/properties/type-element-action-assl.md)|  
|派生要素|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)、 [ReportAction](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)、 [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 アクションの詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](../../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Perspective 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/perspective-element-assl.md)   
 [PerspectiveAction データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
