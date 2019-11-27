---
title: Cláusula Let
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350428"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="f13d1-102">Cláusula Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f13d1-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="f13d1-103">Computa um valor e o atribui a uma nova variável dentro da consulta.</span><span class="sxs-lookup"><span data-stu-id="f13d1-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f13d1-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="f13d1-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f13d1-105">Parts</span></span>  
  
|<span data-ttu-id="f13d1-106">Termo</span><span class="sxs-lookup"><span data-stu-id="f13d1-106">Term</span></span>|<span data-ttu-id="f13d1-107">Definição</span><span class="sxs-lookup"><span data-stu-id="f13d1-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="f13d1-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f13d1-108">Required.</span></span> <span data-ttu-id="f13d1-109">Um alias que pode ser usado para referenciar os resultados da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="f13d1-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="f13d1-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f13d1-110">Required.</span></span> <span data-ttu-id="f13d1-111">Uma expressão que será avaliada e atribuída à variável especificada.</span><span class="sxs-lookup"><span data-stu-id="f13d1-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f13d1-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f13d1-112">Remarks</span></span>  
 <span data-ttu-id="f13d1-113">A cláusula `Let` permite que você calcule valores para cada resultado da consulta e faça referência a eles usando um alias.</span><span class="sxs-lookup"><span data-stu-id="f13d1-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="f13d1-114">O alias pode ser usado em outras cláusulas, como a cláusula `Where`.</span><span class="sxs-lookup"><span data-stu-id="f13d1-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="f13d1-115">A cláusula `Let` permite que você crie uma instrução de consulta que seja mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluído na consulta e substituir o alias sempre que a cláusula de expressão for usada.</span><span class="sxs-lookup"><span data-stu-id="f13d1-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="f13d1-116">Você pode incluir qualquer número de atribuições de `variable` e `expression` na cláusula `Let`.</span><span class="sxs-lookup"><span data-stu-id="f13d1-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="f13d1-117">Separe cada atribuição com uma vírgula (,).</span><span class="sxs-lookup"><span data-stu-id="f13d1-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f13d1-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f13d1-118">Example</span></span>  
 <span data-ttu-id="f13d1-119">O exemplo de código a seguir usa a cláusula `Let` para calcular um desconto de 10% nos produtos.</span><span class="sxs-lookup"><span data-stu-id="f13d1-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="f13d1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f13d1-120">See also</span></span>

- [<span data-ttu-id="f13d1-121">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f13d1-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f13d1-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="f13d1-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="f13d1-123">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="f13d1-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="f13d1-124">Cláusula From</span><span class="sxs-lookup"><span data-stu-id="f13d1-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="f13d1-125">Cláusula Where</span><span class="sxs-lookup"><span data-stu-id="f13d1-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
