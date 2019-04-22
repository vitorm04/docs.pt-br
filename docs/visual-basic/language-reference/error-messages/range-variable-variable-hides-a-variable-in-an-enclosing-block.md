---
title: A variável de intervalo <variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: e31f728de228bea743f6c7b5cbfef3cd73367262
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822707"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="de35e-102">Variável de intervalo \<variável > oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="de35e-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="de35e-103">Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula duplique o nome de uma variável de intervalo já especificado anteriormente na consulta ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.</span><span class="sxs-lookup"><span data-stu-id="de35e-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="de35e-104">**ID do erro:** BC36633</span><span class="sxs-lookup"><span data-stu-id="de35e-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="de35e-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="de35e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="de35e-106">Certifique-se de que todas as variáveis de intervalo em um escopo de consulta em particular tenham nomes exclusivos.</span><span class="sxs-lookup"><span data-stu-id="de35e-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="de35e-107">Você pode colocar uma consulta entre parênteses para garantir que as consultas aninhadas têm um escopo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="de35e-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de35e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de35e-108">See also</span></span>

- [<span data-ttu-id="de35e-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de35e-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="de35e-110">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="de35e-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="de35e-111">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="de35e-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="de35e-112">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="de35e-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="de35e-113">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="de35e-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
