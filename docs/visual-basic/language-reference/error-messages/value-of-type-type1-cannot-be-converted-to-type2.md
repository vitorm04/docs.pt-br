---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8c80429db618e1bcadce1a58a6514d625f0b3cf1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870228"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Valor do tipo 'type1' não pode ser convertido em 'type2'

O valor do tipo ' type1 ' não pode ser convertido em ' type2 '. Você pode usar a propriedade ' value ' para obter o valor da cadeia de caracteres do primeiro elemento de ' \<parentElement> '.  
  
 Foi feita uma tentativa de converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.  
  
 **ID do erro:** BC31194  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use a `Value` Propriedade do literal XML para referenciar seu valor como um `String` . Use a `CType` função, outra função de conversão de tipo ou a <xref:System.Convert> classe para converter o valor como o tipo especificado.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Convert>
- [Funções de conversão do tipo](../functions/type-conversion-functions.md)
- [Literais XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
