---
title: '&#39;Para cada&#39; no tipo &#39; &lt;typename&gt; &#39; é ambíguo porque o tipo implementa várias instanciações de &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81cb37cc4b61fa96e64f59150d95356b2fb0a355
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="d8ba2-102">&#39;Para cada&#39; no tipo &#39; &lt;typename&gt; &#39; é ambíguo porque o tipo implementa várias instanciações de &#39;System.Collections.Generic.IEnumerable (Of T)&#39;</span><span class="sxs-lookup"><span data-stu-id="d8ba2-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="d8ba2-103">Um `For Each` instrução Especifica uma variável de iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d8ba2-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="d8ba2-104">A variável de iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface em um do `Collections` namespaces do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8ba2-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="d8ba2-105">É possível que uma classe implementar mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção.</span><span class="sxs-lookup"><span data-stu-id="d8ba2-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="d8ba2-106">Se uma classe que faz isso é usada para a variável de iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d8ba2-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="d8ba2-107">Nesse caso, o Visual Basic não pode escolher qual método de chamada.</span><span class="sxs-lookup"><span data-stu-id="d8ba2-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="d8ba2-108">**ID do erro:** BC32096</span><span class="sxs-lookup"><span data-stu-id="d8ba2-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8ba2-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d8ba2-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d8ba2-110">Use [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) para converter o tipo de variável de iterador para definir a interface de <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="d8ba2-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ba2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8ba2-111">See Also</span></span>  
 [<span data-ttu-id="d8ba2-112">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="d8ba2-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="d8ba2-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d8ba2-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
