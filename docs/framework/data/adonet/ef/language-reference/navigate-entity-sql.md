---
title: NAVEGAR (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a860fae543e4d74e2b0569ed3672f3dc113f84c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="d0dc7-102">NAVEGAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d0dc7-102">NAVIGATE (Entity SQL)</span></span>
<span data-ttu-id="d0dc7-103">Navega sobre a relação entre estabelecida entidades.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-103">Navigates over the relationship established between entities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0dc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0dc7-104">Syntax</span></span>  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0dc7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d0dc7-105">Arguments</span></span>  
 `instance-expresssion`  
 <span data-ttu-id="d0dc7-106">Uma instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-106">An instance of an entity.</span></span>  
  
 `relationship-type`  
 <span data-ttu-id="d0dc7-107">O nome do tipo de relação, o arquivo de (CSDL) de linguagem de definição de esquema conceitual.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-107">The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="d0dc7-108">O `relationship-type` é qualificado como \<namespace >.\< nome do tipo de relação >.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>  
  
 `to`  
 <span data-ttu-id="d0dc7-109">O final da relação.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-109">The end of the relationship.</span></span>  
  
 `from`  
 <span data-ttu-id="d0dc7-110">O início da relação.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-110">The beginning of the relationship.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0dc7-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d0dc7-111">Return Value</span></span>  
 <span data-ttu-id="d0dc7-112">Se a cardinalidade da finalizar é 1, o valor de retorno será `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="d0dc7-113">Se a cardinalidade da finalizar é, no valor de retorno será `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0dc7-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0dc7-114">Remarks</span></span>  
 <span data-ttu-id="d0dc7-115">As relações são construções de primeira classe em [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span><span class="sxs-lookup"><span data-stu-id="d0dc7-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="d0dc7-116">As relações podem ser estabelecidas entre dois ou mais tipos de entidade, e os usuários podem navegar sobre a relação de fim (entidade) para outra.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="d0dc7-117">`from` e `to` condicional são opcionais quando não há nenhuma ambiguidade na resolução de nomes dentro da relação.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>  
  
 <span data-ttu-id="d0dc7-118">NAVIGATE é válido no espaço de C e de 2.0.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-118">NAVIGATE is valid in O and C space.</span></span>  
  
 <span data-ttu-id="d0dc7-119">O formulário geral de uma compilação de navegação é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d0dc7-119">The general form of a navigation construct is the following:</span></span>  
  
 <span data-ttu-id="d0dc7-120">navegue (`instance-expresssion`, `relationship-type`, [ `to-end` , `from-end` ] [])</span><span class="sxs-lookup"><span data-stu-id="d0dc7-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>  
  
 <span data-ttu-id="d0dc7-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d0dc7-121">For example:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="d0dc7-122">Onde OrderCustomer está `relationship`, e o cliente e ordem são `to-end` (cliente) e `from-end` (ordem) da relação.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="d0dc7-123">Se OrderCustomer foi uma relação n:1, o tipo de resultado da expressão navegar é Ref\<cliente >.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>  
  
 <span data-ttu-id="d0dc7-124">A forma mais simples desta expressão é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d0dc7-124">The simpler form of this expression is the following:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="d0dc7-125">Da mesma forma, em uma consulta do formulário a seguir, a expressão de navegar produziria uma coleção < Ref\<ordem >>.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 <span data-ttu-id="d0dc7-126">A instância expressão deve ser um tipo de entidade/referência.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-126">The instance-expression must be an entity/ref type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0dc7-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0dc7-127">Example</span></span>  
 <span data-ttu-id="d0dc7-128">A seguinte consulta SQL Entity usa o operador NAVEGAR IN para navegar sobre o relacionamento estabelecido entre tipos de entidade de endereço e de SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="d0dc7-129">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d0dc7-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d0dc7-130">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d0dc7-130">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d0dc7-131">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d0dc7-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d0dc7-132">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="d0dc7-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a><span data-ttu-id="d0dc7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0dc7-133">See Also</span></span>  
 [<span data-ttu-id="d0dc7-134">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d0dc7-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d0dc7-135">Como: navegar relações com o operador de navegar</span><span class="sxs-lookup"><span data-stu-id="d0dc7-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
