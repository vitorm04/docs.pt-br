---
title: As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874563"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz

Você tentou declarar uma constante como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico recipiente.  
  
 Constantes devem ser de um tipo intrínseco (,,,,,,,, `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` , `Short` , `Single` ,,, `String` `UInteger` `ULong` , ou `UShort` ), ou um `Enum` tipo com base em um dos tipos integrais.  
  
 **ID do erro:** BC30424  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Declare a constante como um tipo intrínseco ou `Enum` .  
  
2. Uma constante também pode ser um valor especial, como `True` , `False` ou `Nothing` . O compilador considera esses valores predefinidos como sendo do tipo intrínseco apropriado.  
  
## <a name="see-also"></a>Confira também

- [Constantes e enumerações](../constants-and-enumerations.md)
- [Data Types](../../programming-guide/language-features/data-types/index.md)
- [Data Types](../data-types/index.md)
