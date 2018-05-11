---
title: Literais nulos e inferência de tipo (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 74ff2b459488f896c5ea6af4f7d1e045da5a7983
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="0a4a1-102">Literais nulos e inferência de tipo (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0a4a1-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="0a4a1-103">Literais nulos são compatíveis com qualquer no sistema de tipos de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a4a1-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="0a4a1-104">No entanto, para o tipo de um literal nulo para ser inferido corretamente, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] impõe determinadas restrições em um literal nulo pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="0a4a1-105">Tipado nulos</span><span class="sxs-lookup"><span data-stu-id="0a4a1-105">Typed Nulls</span></span>  
 <span data-ttu-id="0a4a1-106">Tipado anula pode ser usado em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="0a4a1-107">Inferência de tipos não é necessária para tipado anula porque o tipo é conhecido.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="0a4a1-108">Por exemplo, você pode construir um zero do tipo Int16 com a seguir compilação de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="0a4a1-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="0a4a1-109">Literais nulos de flutuante</span><span class="sxs-lookup"><span data-stu-id="0a4a1-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="0a4a1-110">Literais nulos de flutuante podem ser usados nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="0a4a1-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="0a4a1-111">Como um argumento para uma expressão de CAST ou de DELEITE.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="0a4a1-112">Essa é a maneira recomendada para gerar uma expressão nula tipada.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="0a4a1-113">Como um argumento para um método ou a uma função.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-113">As an argument to a method or a function.</span></span> <span data-ttu-id="0a4a1-114">As regras padrões de sobrecarga se aplicam.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="0a4a1-115">Como um dos argumentos para uma expressão aritmética como +, -, ou a/.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="0a4a1-116">Os outros argumentos não podem ser nulos literais, se não inferência de tipos não é possível.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="0a4a1-117">Como alguns dos argumentos para uma expressão (lógica AND, OU, ou NÃO).</span><span class="sxs-lookup"><span data-stu-id="0a4a1-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="0a4a1-118">Todos os argumentos são conhecidos para ser do tipo booleano.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="0a4a1-119">Como o argumento para o É NULL ou NÃO É expressão NULA.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="0a4a1-120">Como um ou mais dos argumentos a GOSTE da expressão.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="0a4a1-121">Todos os argumentos sejam cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="0a4a1-122">Como um ou mais dos argumentos para um construtor de nomeadas tipo.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="0a4a1-123">Como um ou mais dos argumentos para um construtor de multiset.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="0a4a1-124">Pelo menos um argumento para o construtor de multiset deve ser uma expressão que não seja um literal nulo.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="0a4a1-125">Como uma ou mais de ENTÃO DE ou em expressões em uma expressão de CASOS.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="0a4a1-126">Pelo menos uma de ENTÃO DE ou em expressões na expressão de CASOS deve ser uma expressão que não seja um literal nulo.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="0a4a1-127">Literais nulos de flutuante não podem ser usados em outros cenários.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="0a4a1-128">Por exemplo, não podem ser usados como argumentos para um construtor de linha.</span><span class="sxs-lookup"><span data-stu-id="0a4a1-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4a1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a4a1-129">See Also</span></span>  
 [<span data-ttu-id="0a4a1-130">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0a4a1-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
