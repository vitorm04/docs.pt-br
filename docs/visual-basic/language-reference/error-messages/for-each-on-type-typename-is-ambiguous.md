---
title: "'For Each' no tipo '<typename>' é ambíguo porque o tipo implementa várias instâncias de 'System.Collections.Generic.IEnumerable(Of T)'"
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801459"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>'For Each' no tipo '\<typename >' é ambíguo porque o tipo implementa várias instanciações de 'System.Collections.Generic.IEnumerable (Of T)'
Um `For Each` declaração especifica uma variável do iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.  
  
 A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface em um dos `Collections` namespaces do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. É possível que uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção. Se uma classe que faz isso é usada para a variável de iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método. Nesse caso, o Visual Basic não pode escolher qual método chamar.  
  
 **ID do erro:** BC32096  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) converter o tipo de variável de iterador à definição de interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.  
  
## <a name="see-also"></a>Consulte também

- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
