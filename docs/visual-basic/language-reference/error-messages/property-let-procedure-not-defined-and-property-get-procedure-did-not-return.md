---
title: Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 65bd2e5cf9c6bbc2d9198dd7fc8947c5a17aa9e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597132"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
Determinadas propriedades, métodos e operações só podem aplicar a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva a coleções, mas o objeto não é uma coleção.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a ortografia do nome do objeto ou propriedade, ou verifique se o objeto é um `Collection` objeto.  
  
2.  Examinar o `Add` método usado para adicionar o objeto à coleção para certificar-se de que a sintaxe está correto e que todos os identificadores foram escritos corretamente.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Collection>
