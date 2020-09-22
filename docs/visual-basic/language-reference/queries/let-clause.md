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
ms.openlocfilehash: a6ff3fc80a2b6752c61a8b8f7d4ce62b5a46baad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869879"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="414d7-102">Cláusula Let (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="414d7-102">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="414d7-103">Computa um valor e o atribui a uma nova variável dentro da consulta.</span><span class="sxs-lookup"><span data-stu-id="414d7-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="414d7-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="414d7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="414d7-105">Parts</span></span>  
  
|<span data-ttu-id="414d7-106">Termo</span><span class="sxs-lookup"><span data-stu-id="414d7-106">Term</span></span>|<span data-ttu-id="414d7-107">Definição</span><span class="sxs-lookup"><span data-stu-id="414d7-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="414d7-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="414d7-108">Required.</span></span> <span data-ttu-id="414d7-109">Um alias que pode ser usado para referenciar os resultados da expressão fornecida.</span><span class="sxs-lookup"><span data-stu-id="414d7-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="414d7-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="414d7-110">Required.</span></span> <span data-ttu-id="414d7-111">Uma expressão que será avaliada e atribuída à variável especificada.</span><span class="sxs-lookup"><span data-stu-id="414d7-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="414d7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="414d7-112">Remarks</span></span>  

 <span data-ttu-id="414d7-113">A `Let` cláusula permite que você calcule valores para cada resultado de consulta e faça referência a eles usando um alias.</span><span class="sxs-lookup"><span data-stu-id="414d7-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="414d7-114">O alias pode ser usado em outras cláusulas, como a `Where` cláusula.</span><span class="sxs-lookup"><span data-stu-id="414d7-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="414d7-115">A `Let` cláusula permite que você crie uma instrução de consulta que seja mais fácil de ler, pois você pode especificar um alias para uma cláusula de expressão incluído na consulta e substituir o alias sempre que a cláusula de expressão for usada.</span><span class="sxs-lookup"><span data-stu-id="414d7-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="414d7-116">Você pode incluir qualquer número de `variable` `expression` atribuições e na `Let` cláusula.</span><span class="sxs-lookup"><span data-stu-id="414d7-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="414d7-117">Separe cada atribuição com uma vírgula (,).</span><span class="sxs-lookup"><span data-stu-id="414d7-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="414d7-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="414d7-118">Example</span></span>  

 <span data-ttu-id="414d7-119">O exemplo de código a seguir usa a `Let` cláusula para calcular um desconto de 10% nos produtos.</span><span class="sxs-lookup"><span data-stu-id="414d7-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="414d7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="414d7-120">See also</span></span>

- [<span data-ttu-id="414d7-121">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="414d7-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="414d7-122">Consultas</span><span class="sxs-lookup"><span data-stu-id="414d7-122">Queries</span></span>](index.md)
- [<span data-ttu-id="414d7-123">Cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="414d7-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="414d7-124">Cláusula from</span><span class="sxs-lookup"><span data-stu-id="414d7-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="414d7-125">Cláusula WHERE</span><span class="sxs-lookup"><span data-stu-id="414d7-125">Where Clause</span></span>](where-clause.md)
