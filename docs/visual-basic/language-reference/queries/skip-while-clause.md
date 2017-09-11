---
title: "Ignorar cláusula While (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
dev_langs:
- VB
helpviewer_keywords:
- Skip While statement
- Skip While clause
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
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
ms.openlocfilehash: 09ecc91e8f82acd2b54785039fbe9c510482f9f4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="956ad-102">Ignorar cláusula While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="956ad-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="956ad-103">Ignora elementos em uma coleção desde que uma condição especificada for `true` e, em seguida, retorna os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="956ad-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="956ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="956ad-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="956ad-105">Partes</span><span class="sxs-lookup"><span data-stu-id="956ad-105">Parts</span></span>  
  
|<span data-ttu-id="956ad-106">Termo</span><span class="sxs-lookup"><span data-stu-id="956ad-106">Term</span></span>|<span data-ttu-id="956ad-107">Definição</span><span class="sxs-lookup"><span data-stu-id="956ad-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="956ad-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="956ad-108">Required.</span></span> <span data-ttu-id="956ad-109">Uma expressão que representa uma condição para testar elementos.</span><span class="sxs-lookup"><span data-stu-id="956ad-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="956ad-110">A expressão deve retornar um `Boolean` valor ou um funcional equivalente, como um `Integer` seja avaliada como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="956ad-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="956ad-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="956ad-111">Remarks</span></span>  
 <span data-ttu-id="956ad-112">O `Skip While` cláusula ignora elementos do começo do resultado de uma consulta até fornecido `expression` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="956ad-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="956ad-113">Depois de `expression` retorna `false`, a consulta retorna todos os elementos restantes.</span><span class="sxs-lookup"><span data-stu-id="956ad-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="956ad-114">O `expression` é ignorada para os resultados restantes.</span><span class="sxs-lookup"><span data-stu-id="956ad-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="956ad-115">O `Skip While` cláusula difere do `Where` cláusula em que o `Where` cláusula pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma condição específica.</span><span class="sxs-lookup"><span data-stu-id="956ad-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="956ad-116">O `Skip While` cláusula excluir elementos apenas até a primeira vez que a condição não for atendida.</span><span class="sxs-lookup"><span data-stu-id="956ad-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="956ad-117">O `Skip While` cláusula é mais útil quando você estiver trabalhando com um resultado de consulta ordenado.</span><span class="sxs-lookup"><span data-stu-id="956ad-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="956ad-118">Você pode ignorar um número específico de resultados desde o início de uma consulta usando o `Skip` cláusula.</span><span class="sxs-lookup"><span data-stu-id="956ad-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="956ad-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="956ad-119">Example</span></span>  
 <span data-ttu-id="956ad-120">O seguinte exemplo de código usa o `Skip While` cláusula para ignorar resultados até que o primeiro cliente dos Estados Unidos é encontrado.</span><span class="sxs-lookup"><span data-stu-id="956ad-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 <span data-ttu-id="956ad-121">[!code-vb[VbSimpleQuerySamples n º&3;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="956ad-121">[!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="956ad-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="956ad-122">See Also</span></span>  
 <span data-ttu-id="956ad-123">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-123">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="956ad-124"> [Consultas](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-124"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="956ad-125"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-125"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="956ad-126"> [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-126"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="956ad-127"> [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-127"> [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="956ad-128"> [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="956ad-128"> [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md) </span></span>  
<span data-ttu-id="956ad-129"> [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="956ad-129"> [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)</span></span>
