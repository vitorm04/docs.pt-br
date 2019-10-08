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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004733"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="684f5-102">Cláusula Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="684f5-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="684f5-103">Computa um valor e o atribui a uma nova variável dentro da consulta.</span><span class="sxs-lookup"><span data-stu-id="684f5-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="684f5-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="684f5-105">Partes</span><span class="sxs-lookup"><span data-stu-id="684f5-105">Parts</span></span>  
  
|<span data-ttu-id="684f5-106">Termo</span><span class="sxs-lookup"><span data-stu-id="684f5-106">Term</span></span>|<span data-ttu-id="684f5-107">Definição</span><span class="sxs-lookup"><span data-stu-id="684f5-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="684f5-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="684f5-108">Required.</span></span> <span data-ttu-id="684f5-109">Um alias que pode ser usado para referenciar os resultados da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="684f5-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="684f5-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="684f5-110">Required.</span></span> <span data-ttu-id="684f5-111">Uma expressão que será avaliada e atribuída à variável especificada.</span><span class="sxs-lookup"><span data-stu-id="684f5-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="684f5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="684f5-112">Remarks</span></span>  
 <span data-ttu-id="684f5-113">A cláusula `Let` permite que você calcule valores para cada resultado da consulta e faça referência a eles usando um alias.</span><span class="sxs-lookup"><span data-stu-id="684f5-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="684f5-114">O alias pode ser usado em outras cláusulas, como a cláusula `Where`.</span><span class="sxs-lookup"><span data-stu-id="684f5-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="684f5-115">A cláusula `Let` permite que você crie uma instrução de consulta que seja mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluído na consulta e substituir o alias sempre que a cláusula de expressão for usada.</span><span class="sxs-lookup"><span data-stu-id="684f5-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="684f5-116">Você pode incluir qualquer número de atribuições `variable` e `expression` na cláusula `Let`.</span><span class="sxs-lookup"><span data-stu-id="684f5-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="684f5-117">Separe cada atribuição com uma vírgula (,).</span><span class="sxs-lookup"><span data-stu-id="684f5-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="684f5-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="684f5-118">Example</span></span>  
 <span data-ttu-id="684f5-119">O exemplo de código a seguir usa a cláusula `Let` para calcular um desconto de 10% nos produtos.</span><span class="sxs-lookup"><span data-stu-id="684f5-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="684f5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="684f5-120">See also</span></span>

- [<span data-ttu-id="684f5-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="684f5-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="684f5-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="684f5-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="684f5-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="684f5-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="684f5-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="684f5-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="684f5-125">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="684f5-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
