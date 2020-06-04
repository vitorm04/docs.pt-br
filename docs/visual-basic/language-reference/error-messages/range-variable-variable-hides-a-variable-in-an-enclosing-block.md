---
title: A variável de intervalo <variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400390"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="348b8-102">A variável de intervalo \<variable> oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="348b8-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="348b8-103">Um nome de variável de intervalo especificado em uma `Select` cláusula,, `From` `Aggregate` ou `Let` duplica o nome de uma variável de intervalo já especificada anteriormente na consulta ou o nome de uma variável que é implicitamente declarada pela consulta, como um nome de campo ou o nome de uma função de agregação.</span><span class="sxs-lookup"><span data-stu-id="348b8-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="348b8-104">**ID do erro:** BC36633</span><span class="sxs-lookup"><span data-stu-id="348b8-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="348b8-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="348b8-105">To correct this error</span></span>  
  
- <span data-ttu-id="348b8-106">Verifique se todas as variáveis de intervalo em um determinado escopo de consulta têm nomes exclusivos.</span><span class="sxs-lookup"><span data-stu-id="348b8-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="348b8-107">Você pode colocar uma consulta entre parênteses para garantir que as consultas aninhadas tenham um escopo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="348b8-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348b8-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="348b8-108">See also</span></span>

- [<span data-ttu-id="348b8-109">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="348b8-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="348b8-110">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="348b8-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="348b8-111">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="348b8-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="348b8-112">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="348b8-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="348b8-113">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="348b8-113">Select Clause</span></span>](../queries/select-clause.md)
