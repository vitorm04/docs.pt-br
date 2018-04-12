---
title: "&#39; Personalizar &#39; o modificador ' não é válido em eventos declarados sem tipos delegados explícitos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39; Personalizar &#39; o modificador ' não é válido em eventos declarados sem tipos delegados explícitos
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
