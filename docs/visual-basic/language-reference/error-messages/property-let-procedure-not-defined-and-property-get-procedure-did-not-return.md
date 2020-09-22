---
title: Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871095"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto

Determinadas propriedades, métodos e operações só podem ser aplicadas a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva para coleções, mas o objeto não é uma coleção.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique a ortografia do nome do objeto ou da propriedade ou verifique se o objeto é um `Collection` objeto.  
  
2. Examine o `Add` método usado para adicionar o objeto à coleção para ter certeza de que a sintaxe está correta e que todos os identificadores foram digitados corretamente.  
  
## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.Collection>
