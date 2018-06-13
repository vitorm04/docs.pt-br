---
title: DOTIPO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: e33d613f290338d63a232bf78e7ebd0826c19897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764116"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="f9967-102">DOTIPO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f9967-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="f9967-103">Retorna uma coleção de objetos de uma expressão de consulta que é de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="f9967-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9967-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9967-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9967-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f9967-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f9967-106">Qualquer expressão de consulta válida que retorna uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="f9967-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="f9967-107">O tipo para testar cada objeto retornado por `expression` contra.</span><span class="sxs-lookup"><span data-stu-id="f9967-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="f9967-108">O tipo deve ser qualificado por um namespace.</span><span class="sxs-lookup"><span data-stu-id="f9967-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9967-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9967-109">Return Value</span></span>  
 <span data-ttu-id="f9967-110">Uma coleção de objetos que são do tipo `test_type`, ou um tipo base ou um tipo derivado de `test_type`.</span><span class="sxs-lookup"><span data-stu-id="f9967-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="f9967-111">Se for especificado SOMENTE, somente as instâncias de `test_type` ou de uma coleção vazia serão retornadas.</span><span class="sxs-lookup"><span data-stu-id="f9967-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9967-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9967-112">Remarks</span></span>  
 <span data-ttu-id="f9967-113">Uma expressão de `OFTYPE` especifica uma expressão que é emitida para executar um teste de tipo versus cada elemento de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f9967-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="f9967-114">A expressão de `OFTYPE` gerencia uma nova coleção do tipo especificado que contém somente os elementos que foram qualquer equivalente a esse tipo ou um subpropriedades tipo deles.</span><span class="sxs-lookup"><span data-stu-id="f9967-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="f9967-115">Uma expressão de `OFTYPE` é uma abreviação de expressão de consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="f9967-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="f9967-116">Já que um gerente é um subtipo de funcionários, a seguinte expressão gerenciar uma coleção somente de gerentes de uma coleção de funcionários:</span><span class="sxs-lookup"><span data-stu-id="f9967-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f9967-117">Também é possível gerar a conversão uma coleção usando o filtro de tipo:</span><span class="sxs-lookup"><span data-stu-id="f9967-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f9967-118">Desde que os executivos são gerentes, a coleção resultante ainda contém todos os executivos originais, embora a coleção é digitada agora como uma coleção de gerentes.</span><span class="sxs-lookup"><span data-stu-id="f9967-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="f9967-119">A tabela a seguir mostra o comportamento do operador de `OFTYPE` sobre alguns padrões.</span><span class="sxs-lookup"><span data-stu-id="f9967-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="f9967-120">Todas as exceções são geradas do lado do cliente antes que o provedor foi chamado:</span><span class="sxs-lookup"><span data-stu-id="f9967-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="f9967-121">Padrão</span><span class="sxs-lookup"><span data-stu-id="f9967-121">Pattern</span></span>|<span data-ttu-id="f9967-122">Comportamento</span><span class="sxs-lookup"><span data-stu-id="f9967-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f9967-123">OFTYPE (coleção (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="f9967-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="f9967-124">Coleção (EntityType)</span><span class="sxs-lookup"><span data-stu-id="f9967-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="f9967-125">OFTYPE (coleção (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f9967-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="f9967-126">Gera</span><span class="sxs-lookup"><span data-stu-id="f9967-126">Throws</span></span>|  
|<span data-ttu-id="f9967-127">OFTYPE (coleção (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="f9967-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="f9967-128">Gera</span><span class="sxs-lookup"><span data-stu-id="f9967-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f9967-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9967-129">Example</span></span>  
 <span data-ttu-id="f9967-130">O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa o operador OFTYPE para retornar uma coleção de objetos OnsiteCourse de uma coleção do curso objetos.</span><span class="sxs-lookup"><span data-stu-id="f9967-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="f9967-131">A consulta se baseia o [modelo School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="f9967-131">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="f9967-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9967-132">See Also</span></span>  
 [<span data-ttu-id="f9967-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f9967-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
