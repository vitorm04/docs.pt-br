---
title: O valor do tipo &#39;type1&#39; não pode ser convertido em &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602745"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>O valor do tipo &#39;type1&#39; não pode ser convertido em &#39;type2&#39;
O valor do tipo 'type1' não pode ser convertido em 'type2'. Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.  
  
 Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.  
  
 **ID do erro:** BC31194  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`. Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert> classe para converter o valor como o tipo especificado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Convert>  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
