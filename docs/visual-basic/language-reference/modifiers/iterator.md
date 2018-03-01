---
title: Iterador (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a>Iterador (Visual Basic)
Especifica que uma função ou `Get` acessador é um iterador.  
  
## <a name="remarks"></a>Comentários  
 Um *iterador* executa uma iteração personalizada em uma coleção. Um iterador usa o [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção por vez. Quando um `Yield` instrução for atingida, o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Um iterador pode ser implementado como uma função ou um `Get` acessador de uma definição de propriedade. O `Iterator` modificador aparece na declaração da função iterador ou `Get` acessador.  
  
 Chamar um iterador no código do cliente usando um [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 O tipo de retorno da função de um iterador ou `Get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Um iterador não pode conter qualquer `ByRef` parâmetros.  
  
 Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.  
  
 Um iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Uso  
 O `Iterator` modificador pode ser usado nesses contextos:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma função de iterador. A função de iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração do [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterator. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. O `Iterator` modificador é na declaração da propriedade.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [Iteradores](../../programming-guide/concepts/iterators.md)  
 [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
