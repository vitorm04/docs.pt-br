---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 4a0f3eb2b1603899e9acc1273c023ec5d0ed3132
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913330"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Valor do tipo 'type1' não pode ser convertido em 'type2'
Valor do tipo 'type1' não pode ser convertido em 'type2'. Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.  
  
 Tentativa de converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.  
  
 **ID do erro:** BC31194  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`. Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert> classe para converter o valor como o tipo especificado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Convert>
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
