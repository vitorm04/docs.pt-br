---
title: "&quot;For Each&quot; no tipo &quot;&lt;typename&gt;&quot; é ambíguo porque o tipo implementa várias instanciações de &quot;System.Collections.Generic.IEnumerable (Of T)&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
dev_langs:
- VB
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
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
ms.openlocfilehash: 6177b48cdc3bc4085cecb6d73c164684ef1c0bc6
ms.lasthandoff: 03/13/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>'For Each' no tipo '&lt;typename&gt;' é ambíguo porque o tipo implementa várias instanciações de 'System.Collections.Generic.IEnumerable (Of T)'
A `For Each` declaração especifica uma variável de iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A>método.</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
 A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=fullName>ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>interface em um do `Collections` namespaces do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName> É possível para uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção. Se uma classe que faz isso é usada para a variável do iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A>método.</xref:System.Collections.IEnumerable.GetEnumerator%2A> Nesse caso, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível escolher qual método de chamada.  
  
 **ID do erro:** BC32096  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) para converter o tipo de variável de iterador para definir a interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A>método você deseja usar.</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
