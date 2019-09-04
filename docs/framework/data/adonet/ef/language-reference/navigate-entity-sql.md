---
title: NAVEGAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249946"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="5246f-102">NAVEGAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5246f-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="5246f-103">Navega sobre a relação entre estabelecida entidades.</span><span class="sxs-lookup"><span data-stu-id="5246f-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="5246f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5246f-104">Syntax</span></span>

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="5246f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5246f-105">Arguments</span></span>

<span data-ttu-id="5246f-106">`instance-expression`Uma instância de uma entidade.</span><span class="sxs-lookup"><span data-stu-id="5246f-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="5246f-107">`relationship-type`O nome do tipo da relação, do arquivo CSDL (linguagem de definição de esquema conceitual).</span><span class="sxs-lookup"><span data-stu-id="5246f-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="5246f-108">O `relationship-type` é qualificado como \<namespace >.\< nome do tipo de relação >.</span><span class="sxs-lookup"><span data-stu-id="5246f-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="5246f-109">`to`O fim da relação.</span><span class="sxs-lookup"><span data-stu-id="5246f-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="5246f-110">`from`O início da relação.</span><span class="sxs-lookup"><span data-stu-id="5246f-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="5246f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5246f-111">Return Value</span></span>

<span data-ttu-id="5246f-112">Se a cardinalidade da finalizar é 1, o valor de retorno será `Ref<T>`.</span><span class="sxs-lookup"><span data-stu-id="5246f-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="5246f-113">Se a cardinalidade da finalizar é, no valor de retorno será `Collection<Ref<T>>`.</span><span class="sxs-lookup"><span data-stu-id="5246f-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5246f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5246f-114">Remarks</span></span>

<span data-ttu-id="5246f-115">As relações são construções de primeira classe no Modelo de Dados de Entidade (EDM).</span><span class="sxs-lookup"><span data-stu-id="5246f-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="5246f-116">As relações podem ser estabelecidas entre dois ou mais tipos de entidade, e os usuários podem navegar sobre a relação de fim (entidade) para outra.</span><span class="sxs-lookup"><span data-stu-id="5246f-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="5246f-117">`from` e `to` condicional são opcionais quando não há nenhuma ambiguidade na resolução de nomes dentro da relação.</span><span class="sxs-lookup"><span data-stu-id="5246f-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="5246f-118">NAVIGATE é válido no espaço de C e de 2.0.</span><span class="sxs-lookup"><span data-stu-id="5246f-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="5246f-119">O formulário geral de uma compilação de navegação é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5246f-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="5246f-120">navegue (`instance-expression`, `relationship-type`, [ `to-end` , `from-end` ] [])</span><span class="sxs-lookup"><span data-stu-id="5246f-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="5246f-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5246f-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="5246f-122">Onde OrderCustomer está `relationship`, e o cliente e ordem são `to-end` (cliente) e `from-end` (ordem) da relação.</span><span class="sxs-lookup"><span data-stu-id="5246f-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="5246f-123">Se OrderCustomer era uma relação n:1, o tipo de resultado da expressão Navigate é Ref\<Customer >.</span><span class="sxs-lookup"><span data-stu-id="5246f-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="5246f-124">A forma mais simples desta expressão é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5246f-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="5246f-125">Da mesma forma, em uma consulta do formulário a seguir, a expressão Navigate produzirá uma coleção\<< ordem de referência > >.</span><span class="sxs-lookup"><span data-stu-id="5246f-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="5246f-126">A instância expressão deve ser um tipo de entidade/referência.</span><span class="sxs-lookup"><span data-stu-id="5246f-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="5246f-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5246f-127">Example</span></span>

<span data-ttu-id="5246f-128">A seguinte consulta SQL Entity usa o operador NAVEGAR IN para navegar sobre o relacionamento estabelecido entre tipos de entidade de endereço e de SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="5246f-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="5246f-129">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5246f-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5246f-130">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="5246f-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="5246f-131">Siga o procedimento em [como: Executar uma consulta que retorna resultados](../how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.</span><span class="sxs-lookup"><span data-stu-id="5246f-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="5246f-132">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="5246f-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a><span data-ttu-id="5246f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5246f-133">See also</span></span>

- [<span data-ttu-id="5246f-134">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5246f-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5246f-135">Como: Navegar pelas relações com o operador de navegação</span><span class="sxs-lookup"><span data-stu-id="5246f-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
