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
Specifies that a function or `Get` accessor is an iterator.  
  
## <a name="remarks"></a>Comentários  
 An *iterator* performs a custom iteration over a collection. An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time. When a `Yield` statement is reached, the current location in code is retained. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 An iterator can be implemented as a function or as a `Get` accessor of a property definition. The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.  
  
 You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.  
  
 An iterator cannot have any `ByRef` parameters.  
  
 Um iterador não pode ocorrer em um evento, um construtor de instância, um construtor estático ou um destruidor estático.  
  
 An iterator can be an anonymous function. Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Uso  
 The `Iterator` modifier can be used in these contexts:  
  
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Exemplo  
 The following example demonstrates an iterator function. The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function. Cada chamada à função iteradora prossegue para a próxima execução da instrução `Yield` que ocorre durante a próxima iteração do loop `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `Get` que é um iterador. The `Iterator` modifier is in the property declaration.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteradores](../../programming-guide/concepts/iterators.md)
- [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
