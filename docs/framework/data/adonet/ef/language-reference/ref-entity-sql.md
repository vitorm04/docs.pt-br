---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 226a14daa706f6cf0481b752fa03dc95db3eff81
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="ref-entity-sql"></a><span data-ttu-id="ed3ea-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed3ea-102">REF (Entity SQL)</span></span>
<span data-ttu-id="ed3ea-103">Retorna uma referência a uma instância de entidade.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed3ea-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="ed3ea-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed3ea-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ed3ea-106">Qualquer expressão válida que produzir uma instância de um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed3ea-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed3ea-107">Return Value</span></span>  
 <span data-ttu-id="ed3ea-108">Uma referência à instância de entidade especificada.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed3ea-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed3ea-109">Remarks</span></span>  
 <span data-ttu-id="ed3ea-110">Uma referência de entidade consiste da chave de entidade e um nome de conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="ed3ea-111">Porque os conjuntos de entidades diferentes podem ser baseados no mesmo tipo de entidade, uma chave específica de entidade pode aparecer em vários conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="ed3ea-112">No entanto, uma referência de entidade é sempre exclusivo.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="ed3ea-113">Se a expressão de entrada representa um objeto armazenado, uma referência a essa entidade será retornada.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="ed3ea-114">Se a expressão de entrada não é uma entidade armazenado, uma referência nula será retornada.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="ed3ea-115">Se o operador de extração de propriedade (.) é usada para acessar uma propriedade de uma entidade, a referência é desreferenciada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed3ea-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed3ea-116">Example</span></span>  
 <span data-ttu-id="ed3ea-117">A seguinte consulta SQL Entity usa o operador de referência para retornar a referência para um argumento de entidade de entrada.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="ed3ea-118">A mesma consulta desreferencia a referência porque estamos usando uma operação de extração de propriedade (.) para acessar uma propriedade de entidade do produto.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="ed3ea-119">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ed3ea-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed3ea-120">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ed3ea-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed3ea-121">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ed3ea-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="ed3ea-122">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ed3ea-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="ed3ea-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed3ea-123">See Also</span></span>  
 [<span data-ttu-id="ed3ea-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="ed3ea-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="ed3ea-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ed3ea-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="ed3ea-126">KEY</span><span class="sxs-lookup"><span data-stu-id="ed3ea-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="ed3ea-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ed3ea-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="ed3ea-128">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="ed3ea-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
