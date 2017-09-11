---
title: "Cláusula Take While (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTakeWhile
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause
- Take While statement
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
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
ms.openlocfilehash: 49aa56f87a8160f182bf581440af00eff9ca9692
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="57141-102">Cláusula Take While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57141-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="57141-103">Inclui elementos em uma coleção desde que uma condição especificada for `true` e ignora os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="57141-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57141-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57141-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="57141-105">Partes</span><span class="sxs-lookup"><span data-stu-id="57141-105">Parts</span></span>  
  
|<span data-ttu-id="57141-106">Termo</span><span class="sxs-lookup"><span data-stu-id="57141-106">Term</span></span>|<span data-ttu-id="57141-107">Definição</span><span class="sxs-lookup"><span data-stu-id="57141-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="57141-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57141-108">Required.</span></span> <span data-ttu-id="57141-109">Uma expressão que representa uma condição para testar elementos.</span><span class="sxs-lookup"><span data-stu-id="57141-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="57141-110">A expressão deve retornar um `Boolean` valor ou um funcional equivalente, como um `Integer` seja avaliada como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="57141-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57141-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="57141-111">Remarks</span></span>  
 <span data-ttu-id="57141-112">O `Take While` cláusula inclui elementos desde o início de um resultado de consulta até fornecido `expression` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="57141-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="57141-113">Após o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="57141-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="57141-114">O `expression` é ignorada para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="57141-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="57141-115">O `Take While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="57141-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="57141-116">O `Take While` cláusula inclui elementos apenas até a primeira vez que a condição não for atendida.</span><span class="sxs-lookup"><span data-stu-id="57141-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="57141-117">O `Take While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="57141-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57141-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57141-118">Example</span></span>  
 <span data-ttu-id="57141-119">O seguinte exemplo de código usa o `Take While` cláusula para recuperar os resultados até que o primeiro cliente sem qualquer pedido é encontrado.</span><span class="sxs-lookup"><span data-stu-id="57141-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 <span data-ttu-id="57141-120">[!code-vb[VbSimpleQuerySamples n º&2;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="57141-120">[!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57141-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57141-121">See Also</span></span>  
 <span data-ttu-id="57141-122">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="57141-122">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="57141-123"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="57141-123"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="57141-124"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="57141-124"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="57141-125"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="57141-125"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="57141-126"> [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="57141-126"> [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="57141-127"> [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="57141-127"> [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="57141-128"> [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="57141-128"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)</span></span>
