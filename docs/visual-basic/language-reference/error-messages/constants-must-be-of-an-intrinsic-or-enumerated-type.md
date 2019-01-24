---
title: As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 0f4cb04558bf9768de22f432a1c59203643aba6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595833"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
Você tentou declarar uma constante, como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico.  
  
 As constantes devem ser de um tipo intrínseco (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ou `UShort`), ou um `Enum` tipo com base em um dos tipos integrais.  
  
 **ID do erro:** BC30424  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declare a constante como um intrínseco ou `Enum` tipo.  
  
2.  Uma constante pode ser também um valor especial, como `True`, `False`, ou `Nothing`. O compilador considera esses valores predefinidos para ser do tipo intrínseco apropriado.  
  
## <a name="see-also"></a>Consulte também
- [Constantes e Enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
