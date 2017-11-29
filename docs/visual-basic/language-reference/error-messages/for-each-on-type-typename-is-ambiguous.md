---
title: "&#39; Para cada &#39; tipo de &#39; &lt;typename&gt;&#39; é ambíguo porque o tipo implementa várias instanciações de &#39; System.Collections.Generic.IEnumerable (Of T) &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords: BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39; Para cada &#39; tipo de &#39; &lt;typename&gt;&#39; é ambíguo porque o tipo implementa várias instanciações de &#39; System.Collections.Generic.IEnumerable (Of T) &#39;
Um `For Each` instrução Especifica uma variável de iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.  
  
 A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface em um do `Collections` namespaces do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. É possível que uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção. Se uma classe que faz isso é usada para a variável de iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método. Nesse caso, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é possível escolher qual método de chamada.  
  
 **ID do erro:** BC32096  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) para converter o tipo de variável de iterador para definir a interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
