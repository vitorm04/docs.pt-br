---
title: Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="9e257-102">Variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="9e257-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="9e257-103">Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula igual ao nome de uma variável de intervalo já especificado anteriormente na consulta, ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.</span><span class="sxs-lookup"><span data-stu-id="9e257-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="9e257-104">**ID do erro:** BC36633</span><span class="sxs-lookup"><span data-stu-id="9e257-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e257-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9e257-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9e257-106">Certifique-se de que todas as variáveis de intervalo em um escopo de consulta em particular têm nomes exclusivos.</span><span class="sxs-lookup"><span data-stu-id="9e257-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="9e257-107">Você pode colocar uma consulta entre parênteses para garantir que consultas aninhadas têm um escopo único.</span><span class="sxs-lookup"><span data-stu-id="9e257-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e257-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e257-108">See Also</span></span>  
 [<span data-ttu-id="9e257-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e257-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9e257-110">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="9e257-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9e257-111">Cláusula Let</span><span class="sxs-lookup"><span data-stu-id="9e257-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="9e257-112">Cláusula Aggregate</span><span class="sxs-lookup"><span data-stu-id="9e257-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="9e257-113">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="9e257-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
