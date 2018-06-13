---
title: '&#39;Personalizar&#39; modificador não é válido em eventos declarados sem tipos delegados explícitos'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587512"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;Personalizar&#39; modificador não é válido em eventos declarados sem tipos delegados explícitos
Diferentemente de um evento não-personalizado, uma `Custom Event` declaração requer um `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado do evento.  
  
 Eventos personalizados não podem ser definidos com um `As` cláusula explícita tipo delegate e com um parâmetro de lista imediatamente após o nome do evento.  
  
 **ID do erro:** BC31122  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Defina um delegado com a mesma lista de parâmetros que o evento personalizado.  
  
     Por exemplo, se o `Custom Event` foi definido por `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, em seguida, o delegado correspondente seria o seguinte.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Substituir a lista de parâmetros do evento personalizado com um `As` cláusula especificando o tipo delegado.  
  
     Continuando com o exemplo `Custom Event` declaração poderia ser reescrita da seguinte maneira.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo declara um `Custom Event` e especifica necessários `As` cláusula com um tipo delegado.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
