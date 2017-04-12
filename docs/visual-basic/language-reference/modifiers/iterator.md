---
title: Iterador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
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
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8c0041ef995e6969aa8e28381b2446c08588c8f4
ms.lasthandoff: 03/13/2017

---
# <a name="iterator-visual-basic"></a>Iterador (Visual Basic)
Especifica que uma função ou `Get` acessador é um iterador.  
  
## <a name="remarks"></a>Comentários  
 Um *iterador* realiza a uma iteração personalizada em uma coleção. Um iterador usa o [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção por vez. Quando um `Yield` instrução é alcançada, o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Um iterador pode ser implementado como uma função ou um `Get` acessador de uma definição de propriedade. O `Iterator` modificador aparece na declaração da função iterador ou `Get` acessador.  
  
 Chamar um iterador no código do cliente usando um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 O tipo de retorno de uma função de iterador ou `Get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 Um iterador não pode ter nenhum `ByRef` parâmetros.  
  
 Um iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.  
  
 Um iterador pode ser uma função anônima. Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 Para obter mais informações sobre iteradores, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="usage"></a>Uso  
 O `Iterator` modificador pode ser usado nesses contextos:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra uma função do iterador. A função de iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Cada iteração de [para cada](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corpo da instrução no `Main` cria uma chamada para o `Power` função iterador. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 [!code-vb[VbVbalrStatements&#98;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. O `Iterator` modificador é na declaração da propriedade.  
  
 [!code-vb[VbVbalrStatements&#99;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 Para obter exemplos adicionais, consulte [iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute></xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>   
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)   
 [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
