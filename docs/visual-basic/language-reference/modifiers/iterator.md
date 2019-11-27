---
title: Iterador
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351530"
---
# <a name="iterator-visual-basic"></a>Iterador (Visual Basic)
Especifica que uma função ou acessador de `Get` é um iterador.  
  
## <a name="remarks"></a>Comentários  
 Um *iterador* executa uma iteração personalizada em uma coleção. Um iterador usa a instrução [yield](../../../visual-basic/language-reference/statements/yield-statement.md) para retornar cada elemento da coleção um de cada vez. Quando uma instrução `Yield` é atingida, o local atual no código é mantido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Um iterador pode ser implementado como uma função ou como um acessador `Get` de uma definição de propriedade. O modificador de `Iterator` aparece na declaração da função de iterador ou `Get` acessador.  
  
 Você chama um iterador do código do cliente usando um [para cada... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 O tipo de retorno de uma função de iterador ou acessador de `Get` pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Um iterador não pode ter parâmetros de `ByRef`.  
  
 Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.  
  
 Um iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Uso  
 O modificador de `Iterator` pode ser usado nesses contextos:  
  
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma função de iterador. A função Iterator tem uma instrução `Yield` que está dentro de um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração do corpo da instrução [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) no `Main` cria uma chamada para a função de iterador `Power`. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. O modificador de `Iterator` está na declaração de propriedade.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteradores](../../programming-guide/concepts/iterators.md)
- [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
