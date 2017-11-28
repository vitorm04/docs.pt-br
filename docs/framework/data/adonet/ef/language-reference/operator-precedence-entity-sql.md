---
title: "Precedência do operador (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="42b00-102">Precedência do operador (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="42b00-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="42b00-103">Quando um [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta tem vários operadores, a precedência de operador determina a sequência na qual as operações são executadas.</span><span class="sxs-lookup"><span data-stu-id="42b00-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="42b00-104">A ordem de execução pode impactar significativamente no resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="42b00-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="42b00-105">Os operadores têm os níveis de precedência mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="42b00-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="42b00-106">Um operador com um nível mais alto é avaliada antes de um operador com um nível inferior.</span><span class="sxs-lookup"><span data-stu-id="42b00-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="42b00-107">Nível</span><span class="sxs-lookup"><span data-stu-id="42b00-107">Level</span></span>|<span data-ttu-id="42b00-108">Tipo de operação</span><span class="sxs-lookup"><span data-stu-id="42b00-108">Operation type</span></span>|<span data-ttu-id="42b00-109">Operador</span><span class="sxs-lookup"><span data-stu-id="42b00-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="42b00-110">1</span><span class="sxs-lookup"><span data-stu-id="42b00-110">1</span></span>|<span data-ttu-id="42b00-111">Primária</span><span class="sxs-lookup"><span data-stu-id="42b00-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="42b00-112">2</span><span class="sxs-lookup"><span data-stu-id="42b00-112">2</span></span>|<span data-ttu-id="42b00-113">Unário</span><span class="sxs-lookup"><span data-stu-id="42b00-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="42b00-114">3</span><span class="sxs-lookup"><span data-stu-id="42b00-114">3</span></span>|<span data-ttu-id="42b00-115">Multiplicativo</span><span class="sxs-lookup"><span data-stu-id="42b00-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="42b00-116">4</span><span class="sxs-lookup"><span data-stu-id="42b00-116">4</span></span>|<span data-ttu-id="42b00-117">Aditivo</span><span class="sxs-lookup"><span data-stu-id="42b00-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="42b00-118">5</span><span class="sxs-lookup"><span data-stu-id="42b00-118">5</span></span>|<span data-ttu-id="42b00-119">Ordenando</span><span class="sxs-lookup"><span data-stu-id="42b00-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="42b00-120">6</span><span class="sxs-lookup"><span data-stu-id="42b00-120">6</span></span>|<span data-ttu-id="42b00-121">Igualdade</span><span class="sxs-lookup"><span data-stu-id="42b00-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="42b00-122">7</span><span class="sxs-lookup"><span data-stu-id="42b00-122">7</span></span>|<span data-ttu-id="42b00-123">AND condicional</span><span class="sxs-lookup"><span data-stu-id="42b00-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="42b00-124">8</span><span class="sxs-lookup"><span data-stu-id="42b00-124">8</span></span>|<span data-ttu-id="42b00-125">OR condicional</span><span class="sxs-lookup"><span data-stu-id="42b00-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="42b00-126">Quando dois operadores em uma expressão têm o mesmo nível de precedência de operadores, são avaliados esquerda para a direita, com base na sua posição na consulta.</span><span class="sxs-lookup"><span data-stu-id="42b00-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="42b00-127">Por exemplo, `x+y-z` é avaliado como `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="42b00-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="42b00-128">Você pode usar parênteses para substituir a precedência de operadores definida em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="42b00-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="42b00-129">Todos dentro dos parênteses é avaliado primeiro para produzir um único resultado antes que o resultado pode ser usado por qualquer operador fora dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="42b00-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="42b00-130">Por exemplo, `x+y*z` multiplica `y` por `z` e, em seguida, adiciona `x`, mas `(x+y)*z` adiciona `x` para `y` e, em seguida, multiplica o resultado por `z`.</span><span class="sxs-lookup"><span data-stu-id="42b00-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b00-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42b00-131">See Also</span></span>  
 [<span data-ttu-id="42b00-132">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="42b00-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
