---
title: "'For Each' no tipo '<typename>' é ambíguo porque o tipo implementa várias instâncias de 'System.Collections.Generic.IEnumerable(Of T)'"
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: af2340e8e514391503d5f9b706d13ba93336698e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662113"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="577d2-102">'For Each' no tipo '\<typename >' é ambíguo porque o tipo implementa várias instanciações de 'System.Collections.Generic.IEnumerable (Of T)'</span><span class="sxs-lookup"><span data-stu-id="577d2-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="577d2-103">Um `For Each` declaração especifica uma variável do iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.</span><span class="sxs-lookup"><span data-stu-id="577d2-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="577d2-104">A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface em um dos `Collections` namespaces do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="577d2-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="577d2-105">É possível que uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção.</span><span class="sxs-lookup"><span data-stu-id="577d2-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="577d2-106">Se uma classe que faz isso é usada para a variável de iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.</span><span class="sxs-lookup"><span data-stu-id="577d2-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="577d2-107">Nesse caso, o Visual Basic não pode escolher qual método chamar.</span><span class="sxs-lookup"><span data-stu-id="577d2-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="577d2-108">**ID do erro:** BC32096</span><span class="sxs-lookup"><span data-stu-id="577d2-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="577d2-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="577d2-109">To correct this error</span></span>  
  
- <span data-ttu-id="577d2-110">Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) converter o tipo de variável de iterador à definição de interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="577d2-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577d2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="577d2-111">See also</span></span>

- [<span data-ttu-id="577d2-112">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="577d2-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="577d2-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="577d2-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
