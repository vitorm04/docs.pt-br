---
title: "Propriedade deixa procedimento não definido e procedimento get de propriedade não retornou um objeto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID451
dev_langs:
- VB
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 477f0fc9ee01f4284f070bf68fbd94124d70b64d
ms.lasthandoff: 03/13/2017

---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
Certas propriedades, métodos e operações só podem aplicar a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva a coleções, mas o objeto não é uma coleção.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a ortografia do nome do objeto ou uma propriedade, ou verifique se o objeto é uma `Collection` objeto.  
  
2.  Examinar o `Add`método usado para adicionar o objeto à coleção para certificar-se de que a sintaxe está correto e que quaisquer identificadores foram grafados corretamente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Collection></xref:Microsoft.VisualBasic.Collection>
