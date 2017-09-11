---
title: "A variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
dev_langs:
- VB
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b0d0b93f1d130da2240bacfea44f2664be0345c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="0f841-102">A variável de intervalo &lt;variável&gt; oculta uma variável em um bloco delimitador, uma variável de intervalo definida anteriormente ou uma variável declarada implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="0f841-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="0f841-103">Um nome de variável de intervalo especificado em uma `Select`, `From`, `Aggregate`, ou `Let` cláusula duplique o nome de uma variável de intervalo já especificado anteriormente na consulta, ou o nome de uma variável que é declarado implicitamente pela consulta, como um nome de campo ou o nome de uma função de agregação.</span><span class="sxs-lookup"><span data-stu-id="0f841-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="0f841-104">**ID do erro:** BC36633</span><span class="sxs-lookup"><span data-stu-id="0f841-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f841-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0f841-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0f841-106">Verifique se todas as variáveis de alcance em um escopo de consulta em particular têm nomes exclusivos.</span><span class="sxs-lookup"><span data-stu-id="0f841-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="0f841-107">Você pode delimitar a consulta entre parênteses para garantir que consultas aninhadas têm um escopo exclusivo.</span><span class="sxs-lookup"><span data-stu-id="0f841-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f841-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f841-108">See Also</span></span>  
 <span data-ttu-id="0f841-109">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-109">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="0f841-110"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-110"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="0f841-111"> [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-111"> [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md) </span></span>  
<span data-ttu-id="0f841-112"> [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-112"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="0f841-113"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0f841-113"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)</span></span>
