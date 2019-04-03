---
title: Cláusula Let (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828688"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="388eb-102">Cláusula Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="388eb-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="388eb-103">Calcula um valor e o atribui a uma nova variável dentro da consulta.</span><span class="sxs-lookup"><span data-stu-id="388eb-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="388eb-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="388eb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="388eb-105">Parts</span></span>  
  
|<span data-ttu-id="388eb-106">Termo</span><span class="sxs-lookup"><span data-stu-id="388eb-106">Term</span></span>|<span data-ttu-id="388eb-107">Definição</span><span class="sxs-lookup"><span data-stu-id="388eb-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="388eb-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="388eb-108">Required.</span></span> <span data-ttu-id="388eb-109">Um alias que pode ser usado para referenciar os resultados da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="388eb-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="388eb-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="388eb-110">Required.</span></span> <span data-ttu-id="388eb-111">Uma expressão que será avaliada e atribuída à variável especificada.</span><span class="sxs-lookup"><span data-stu-id="388eb-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="388eb-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="388eb-112">Remarks</span></span>  
 <span data-ttu-id="388eb-113">O `Let` cláusula permite que você calcule valores para cada resultado da consulta e referenciá-los usando um alias.</span><span class="sxs-lookup"><span data-stu-id="388eb-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="388eb-114">O alias pode ser usado em outras cláusulas, como o `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="388eb-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="388eb-115">O `Let` cláusula permite que você crie uma instrução de consulta que é mais fácil de ler porque você pode especificar um alias para uma cláusula de expressão incluída na consulta e substituir o alias de cada vez que a cláusula de expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="388eb-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="388eb-116">Você pode incluir qualquer número de `variable` e `expression` atribuições no `Let` cláusula.</span><span class="sxs-lookup"><span data-stu-id="388eb-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="388eb-117">Separe cada atribuição com uma vírgula (,).</span><span class="sxs-lookup"><span data-stu-id="388eb-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="388eb-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="388eb-118">Example</span></span>  
 <span data-ttu-id="388eb-119">O seguinte exemplo de código usa o `Let` cláusula para 10% de desconto em produtos de computação.</span><span class="sxs-lookup"><span data-stu-id="388eb-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="388eb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="388eb-120">See also</span></span>

- [<span data-ttu-id="388eb-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="388eb-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="388eb-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="388eb-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="388eb-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="388eb-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="388eb-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="388eb-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="388eb-125">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="388eb-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
