---
title: "Valor do tipo &quot;type1&quot; não pode ser convertido em &quot;type2&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
dev_langs:
- VB
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7f6a0bbe489467f4a3ff5f3b2819e819b5daa544
ms.lasthandoff: 03/13/2017

---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Valor do tipo 'type1' não pode ser convertido em 'type2'
Valor do tipo 'type1' não pode ser convertido em 'type2'. Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.  
  
 Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.  
  
 **ID do erro:** BC31194  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`. Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert>classe para converter o valor do tipo especificado.</xref:System.Convert>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Convert></xref:System.Convert>   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
