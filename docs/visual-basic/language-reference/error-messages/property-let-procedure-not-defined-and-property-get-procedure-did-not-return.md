---
title: Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 7da1de98132f47740e805ed34ff3890f0ba0f889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920738"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
Determinadas propriedades, métodos e operações só podem aplicar a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva a coleções, mas o objeto não é uma coleção.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique a ortografia do nome do objeto ou propriedade, ou verifique se o objeto é um `Collection` objeto.  
  
2. Examinar o `Add` método usado para adicionar o objeto à coleção para certificar-se de que a sintaxe está correto e que todos os identificadores foram escritos corretamente.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Collection>
