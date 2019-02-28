---
title: Iterador (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 06188560163491284eab0dcfc4bba6b029e65ce8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969278"
---
# <a name="iterator-visual-basic"></a>Iterador (Visual Basic)
Especifica que uma função ou `Get` acessador é um iterador.  
  
## <a name="remarks"></a>Comentários  
 Uma *iterador* realiza uma iteração personalizada em uma coleção. Um iterador usa a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção por vez. Quando um `Yield` instrução for atingida, o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Um iterador pode ser implementado como uma função ou um `Get` acessador de uma definição de propriedade. O `Iterator` modificador aparece na declaração da função de iterador ou `Get` acessador.  
  
 Você chama um iterador no código do cliente usando um [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 O tipo de retorno de uma função de iterador ou `Get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Um iterador não pode ter nenhum `ByRef` parâmetros.  
  
 Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.  
  
 Um iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Uso  
 O `Iterator` modificador pode ser usado nestes contextos:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma função de iterador. A função de iterador tem uma `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração do [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iteradora. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. O `Iterator` modificador é na declaração da propriedade.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Para obter exemplos adicionais, consulte [iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteradores](../../programming-guide/concepts/iterators.md)
- [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
