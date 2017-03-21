---
title: "O modificador &quot;Custom&quot; não é válido em eventos declarados sem tipos delegados explícitos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
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
ms.openlocfilehash: 0e70fca6a0608df5db43156f70196b4e5c9b2339
ms.lasthandoff: 03/13/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>O modificador 'Custom' não é válido em eventos declarados sem tipos delegados explícitos
Diferentemente de um evento não-personalizado, uma `Custom Event` declaração requer um `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado para o evento.  
  
 Os eventos não-personalizados podem ser definidos com um `As` cláusula e explícito tipo delegado, ou com um parâmetro de lista imediatamente após o nome do evento.  
  
 **ID do erro:** BC31122  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Defina um delegado com a mesma lista de parâmetros que o evento personalizado.  
  
     Por exemplo, se o `Custom Event` foi definido pela `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, então o delegado correspondente viria a seguir.  
  
     [!code-vb[VbVbalrEventError n º&18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Substitua a lista de parâmetros do evento personalizado com um `As` cláusula especificando o tipo de delegado.  
  
     Continuando com o exemplo `Custom Event` declaração poderia ser reescrita da seguinte maneira.  
  
     [!code-vb[19 VbVbalrEventError](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo declara um `Custom Event` e especifica a necessário `As` cláusula com um tipo delegado.  
  
 [!code-vb[VbVbalrEventError n º&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
