---
title: '&#39;Para cada&#39; no tipo &#39; &lt;typename&gt; &#39; é ambíguo porque o tipo implementa várias instanciações de &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 7fd779ba34afa2a59fa6c42971597df8ce01495a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597340"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;Para cada&#39; no tipo &#39; &lt;typename&gt; &#39; é ambíguo porque o tipo implementa várias instanciações de &#39;System.Collections.Generic.IEnumerable (Of T)&#39;
Um `For Each` declaração especifica uma variável do iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.  
  
 A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface em um dos `Collections` namespaces do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. É possível que uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção. Se uma classe que faz isso é usada para a variável de iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método. Nesse caso, o Visual Basic não pode escolher qual método chamar.  
  
 **ID do erro:** BC32096  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) converter o tipo de variável de iterador à definição de interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.  
  
## <a name="see-also"></a>Consulte também
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
