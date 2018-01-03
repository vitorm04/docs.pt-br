---
title: "Literais nulos e inferência de tipo (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5a8b921db06d600430fd4e10466070910119626d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="226e0-102">Literais nulos e inferência de tipo (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="226e0-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="226e0-103">Literais nulos são compatíveis com qualquer no sistema de tipos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="226e0-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="226e0-104">No entanto, para o tipo de um literal nulo para ser inferido corretamente, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impõe determinadas restrições em um literal nulo pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="226e0-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="226e0-105">Tipado nulos</span><span class="sxs-lookup"><span data-stu-id="226e0-105">Typed Nulls</span></span>  
 <span data-ttu-id="226e0-106">Tipado anula pode ser usado em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="226e0-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="226e0-107">Inferência de tipos não é necessária para tipado anula porque o tipo é conhecido.</span><span class="sxs-lookup"><span data-stu-id="226e0-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="226e0-108">Por exemplo, você pode construir um zero do tipo Int16 com a seguir compilação de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="226e0-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="226e0-109">Literais nulos de flutuante</span><span class="sxs-lookup"><span data-stu-id="226e0-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="226e0-110">Literais nulos de flutuante podem ser usados nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="226e0-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="226e0-111">Como um argumento para uma expressão de CAST ou de DELEITE.</span><span class="sxs-lookup"><span data-stu-id="226e0-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="226e0-112">Essa é a maneira recomendada para gerar uma expressão nula tipada.</span><span class="sxs-lookup"><span data-stu-id="226e0-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="226e0-113">Como um argumento para um método ou a uma função.</span><span class="sxs-lookup"><span data-stu-id="226e0-113">As an argument to a method or a function.</span></span> <span data-ttu-id="226e0-114">As regras padrões de sobrecarga se aplicam.</span><span class="sxs-lookup"><span data-stu-id="226e0-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="226e0-115">Como um dos argumentos para uma expressão aritmética como +, -, ou a/.</span><span class="sxs-lookup"><span data-stu-id="226e0-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="226e0-116">Os outros argumentos não podem ser nulos literais, se não inferência de tipos não é possível.</span><span class="sxs-lookup"><span data-stu-id="226e0-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="226e0-117">Como alguns dos argumentos para uma expressão (lógica AND, OU, ou NÃO).</span><span class="sxs-lookup"><span data-stu-id="226e0-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="226e0-118">Todos os argumentos são conhecidos para ser do tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="226e0-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="226e0-119">Como o argumento para o É NULL ou NÃO É expressão NULA.</span><span class="sxs-lookup"><span data-stu-id="226e0-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="226e0-120">Como um ou mais dos argumentos a GOSTE da expressão.</span><span class="sxs-lookup"><span data-stu-id="226e0-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="226e0-121">Todos os argumentos sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="226e0-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="226e0-122">Como um ou mais dos argumentos para um construtor de nomeadas tipo.</span><span class="sxs-lookup"><span data-stu-id="226e0-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="226e0-123">Como um ou mais dos argumentos para um construtor de multiset.</span><span class="sxs-lookup"><span data-stu-id="226e0-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="226e0-124">Pelo menos um argumento para o construtor de multiset deve ser uma expressão que não seja um literal nulo.</span><span class="sxs-lookup"><span data-stu-id="226e0-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="226e0-125">Como uma ou mais de ENTÃO DE ou em expressões em uma expressão de CASOS.</span><span class="sxs-lookup"><span data-stu-id="226e0-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="226e0-126">Pelo menos uma de ENTÃO DE ou em expressões na expressão de CASOS deve ser uma expressão que não seja um literal nulo.</span><span class="sxs-lookup"><span data-stu-id="226e0-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="226e0-127">Literais nulos de flutuante não podem ser usados em outros cenários.</span><span class="sxs-lookup"><span data-stu-id="226e0-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="226e0-128">Por exemplo, não podem ser usados como argumentos para um construtor de linha.</span><span class="sxs-lookup"><span data-stu-id="226e0-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e0-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="226e0-129">See Also</span></span>  
 [<span data-ttu-id="226e0-130">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="226e0-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
