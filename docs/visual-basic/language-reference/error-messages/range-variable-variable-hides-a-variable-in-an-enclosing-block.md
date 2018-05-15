---
title: Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="a10a8-102">Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="a10a8-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="a10a8-103">Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula igual ao nome de uma variável de intervalo já especificado anteriormente na consulta, ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.</span><span class="sxs-lookup"><span data-stu-id="a10a8-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="a10a8-104">**ID do erro:** BC36633</span><span class="sxs-lookup"><span data-stu-id="a10a8-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a10a8-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a10a8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a10a8-106">Certifique-se de que todas as variáveis de intervalo em um escopo de consulta em particular têm nomes exclusivos.</span><span class="sxs-lookup"><span data-stu-id="a10a8-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="a10a8-107">Você pode colocar uma consulta entre parênteses para garantir que consultas aninhadas têm um escopo único.</span><span class="sxs-lookup"><span data-stu-id="a10a8-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10a8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a10a8-108">See Also</span></span>  
 [<span data-ttu-id="a10a8-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a10a8-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="a10a8-110">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="a10a8-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="a10a8-111">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="a10a8-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="a10a8-112">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="a10a8-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="a10a8-113">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="a10a8-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
