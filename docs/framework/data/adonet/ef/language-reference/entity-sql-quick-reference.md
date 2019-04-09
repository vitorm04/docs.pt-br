---
title: Referência rápida de Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207065"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="d9679-102">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9679-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="d9679-103">Este tópico fornece uma referência rápida às consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9679-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="d9679-104">As consultas neste tópico baseiam-se no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d9679-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="d9679-105">Literais</span><span class="sxs-lookup"><span data-stu-id="d9679-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="d9679-106">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="d9679-106">String</span></span>  
 <span data-ttu-id="d9679-107">Há literais de cadeia de caracteres Unicode e não Unicode.</span><span class="sxs-lookup"><span data-stu-id="d9679-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="d9679-108">Cadeias de caracteres Unicode são pré-demarcadas com N. Por exemplo, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="d9679-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="d9679-109">Este é um exemplo de um literal de cadeia de caracteres não Unicode:</span><span class="sxs-lookup"><span data-stu-id="d9679-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="d9679-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-110">Output:</span></span>  
  
|<span data-ttu-id="d9679-111">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-112">hello</span><span class="sxs-lookup"><span data-stu-id="d9679-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="d9679-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="d9679-113">DateTime</span></span>  
 <span data-ttu-id="d9679-114">Em literais DateTime, as partes de data e hora são obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="d9679-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="d9679-115">Não há valor padrão.</span><span class="sxs-lookup"><span data-stu-id="d9679-115">There are no default values.</span></span>  
  
 <span data-ttu-id="d9679-116">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="d9679-117">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-117">Output:</span></span>  
  
|<span data-ttu-id="d9679-118">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="d9679-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="d9679-120">Inteiro</span><span class="sxs-lookup"><span data-stu-id="d9679-120">Integer</span></span>  
 <span data-ttu-id="d9679-121">Literais inteiros podem ser do tipo Int32 (123), UInt32 (123U), Int64 (123L) e UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="d9679-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="d9679-122">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="d9679-123">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-123">Output:</span></span>  
  
|<span data-ttu-id="d9679-124">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-125">1</span><span class="sxs-lookup"><span data-stu-id="d9679-125">1</span></span>|  
|<span data-ttu-id="d9679-126">2</span><span class="sxs-lookup"><span data-stu-id="d9679-126">2</span></span>|  
|<span data-ttu-id="d9679-127">3</span><span class="sxs-lookup"><span data-stu-id="d9679-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="d9679-128">Outros</span><span class="sxs-lookup"><span data-stu-id="d9679-128">Other</span></span>  
 <span data-ttu-id="d9679-129">Outros literais com suporte do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são Guid, Binary, Float/Double, Decimal e `null`.</span><span class="sxs-lookup"><span data-stu-id="d9679-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="d9679-130">Literais nulos em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são considerados compatíveis com cada outro tipo no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="d9679-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="d9679-131">Construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="d9679-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="d9679-132">ROW</span><span class="sxs-lookup"><span data-stu-id="d9679-132">ROW</span></span>  
 <span data-ttu-id="d9679-133">[LINHA](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constrói um valor (registro) anônimo, tipado estruturalmente como em:</span><span class="sxs-lookup"><span data-stu-id="d9679-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in:</span></span> `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 <span data-ttu-id="d9679-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="d9679-135">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-135">Output:</span></span>  
  
|<span data-ttu-id="d9679-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="d9679-136">ProductID</span></span>|<span data-ttu-id="d9679-137">Nome</span><span class="sxs-lookup"><span data-stu-id="d9679-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="d9679-138">1</span><span class="sxs-lookup"><span data-stu-id="d9679-138">1</span></span>|<span data-ttu-id="d9679-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="d9679-139">Adjustable Race</span></span>|  
|<span data-ttu-id="d9679-140">879</span><span class="sxs-lookup"><span data-stu-id="d9679-140">879</span></span>|<span data-ttu-id="d9679-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="d9679-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="d9679-142">712</span><span class="sxs-lookup"><span data-stu-id="d9679-142">712</span></span>|<span data-ttu-id="d9679-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="d9679-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="d9679-144">...</span><span class="sxs-lookup"><span data-stu-id="d9679-144">...</span></span>|<span data-ttu-id="d9679-145">...</span><span class="sxs-lookup"><span data-stu-id="d9679-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="d9679-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="d9679-146">MULTISET</span></span>  
 <span data-ttu-id="d9679-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constrói coleções, tais como:</span><span class="sxs-lookup"><span data-stu-id="d9679-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 <span data-ttu-id="d9679-148">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-148">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="d9679-149">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-149">Output:</span></span>  
  
|<span data-ttu-id="d9679-150">ProductID</span><span class="sxs-lookup"><span data-stu-id="d9679-150">ProductID</span></span>|<span data-ttu-id="d9679-151">Nome</span><span class="sxs-lookup"><span data-stu-id="d9679-151">Name</span></span>|<span data-ttu-id="d9679-152">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="d9679-152">ProductNumber</span></span>|<span data-ttu-id="d9679-153">…</span><span class="sxs-lookup"><span data-stu-id="d9679-153">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="d9679-154">842</span><span class="sxs-lookup"><span data-stu-id="d9679-154">842</span></span>|<span data-ttu-id="d9679-155">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="d9679-155">Touring-Panniers, Large</span></span>|<span data-ttu-id="d9679-156">PA-T100</span><span class="sxs-lookup"><span data-stu-id="d9679-156">PA-T100</span></span>|<span data-ttu-id="d9679-157">…</span><span class="sxs-lookup"><span data-stu-id="d9679-157">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="d9679-158">Objeto</span><span class="sxs-lookup"><span data-stu-id="d9679-158">Object</span></span>  
 <span data-ttu-id="d9679-159">[Chamada de construtor do tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constrói objetos definidos pelo usuário (nomeados), como `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="d9679-159">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="d9679-160">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-160">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="d9679-161">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-161">Output:</span></span>  
  
|<span data-ttu-id="d9679-162">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="d9679-162">SalesOrderDetailID</span></span>|<span data-ttu-id="d9679-163">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="d9679-163">CarrierTrackingNumber</span></span>|<span data-ttu-id="d9679-164">OrderQty</span><span class="sxs-lookup"><span data-stu-id="d9679-164">OrderQty</span></span>|<span data-ttu-id="d9679-165">ProductID</span><span class="sxs-lookup"><span data-stu-id="d9679-165">ProductID</span></span>|<span data-ttu-id="d9679-166">...</span><span class="sxs-lookup"><span data-stu-id="d9679-166">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="d9679-167">1</span><span class="sxs-lookup"><span data-stu-id="d9679-167">1</span></span>|<span data-ttu-id="d9679-168">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="d9679-168">4911-403C-98</span></span>|<span data-ttu-id="d9679-169">1</span><span class="sxs-lookup"><span data-stu-id="d9679-169">1</span></span>|<span data-ttu-id="d9679-170">776</span><span class="sxs-lookup"><span data-stu-id="d9679-170">776</span></span>|<span data-ttu-id="d9679-171">...</span><span class="sxs-lookup"><span data-stu-id="d9679-171">...</span></span>|  
|<span data-ttu-id="d9679-172">2</span><span class="sxs-lookup"><span data-stu-id="d9679-172">2</span></span>|<span data-ttu-id="d9679-173">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="d9679-173">4911-403C-98</span></span>|<span data-ttu-id="d9679-174">3</span><span class="sxs-lookup"><span data-stu-id="d9679-174">3</span></span>|<span data-ttu-id="d9679-175">777</span><span class="sxs-lookup"><span data-stu-id="d9679-175">777</span></span>|<span data-ttu-id="d9679-176">...</span><span class="sxs-lookup"><span data-stu-id="d9679-176">...</span></span>|  
|<span data-ttu-id="d9679-177">...</span><span class="sxs-lookup"><span data-stu-id="d9679-177">...</span></span>|<span data-ttu-id="d9679-178">...</span><span class="sxs-lookup"><span data-stu-id="d9679-178">...</span></span>|<span data-ttu-id="d9679-179">...</span><span class="sxs-lookup"><span data-stu-id="d9679-179">...</span></span>|<span data-ttu-id="d9679-180">...</span><span class="sxs-lookup"><span data-stu-id="d9679-180">...</span></span>|<span data-ttu-id="d9679-181">...</span><span class="sxs-lookup"><span data-stu-id="d9679-181">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="d9679-182">Referências</span><span class="sxs-lookup"><span data-stu-id="d9679-182">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d9679-183">REF</span><span class="sxs-lookup"><span data-stu-id="d9679-183">REF</span></span>  
 <span data-ttu-id="d9679-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) cria uma referência a uma instância do tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="d9679-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="d9679-185">Por exemplo, a seguinte consulta retorna referências para cada entidade Order no conjunto de entidades Orders:</span><span class="sxs-lookup"><span data-stu-id="d9679-185">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="d9679-186">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-186">Output:</span></span>  
  
|<span data-ttu-id="d9679-187">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-187">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-188">1</span><span class="sxs-lookup"><span data-stu-id="d9679-188">1</span></span>|  
|<span data-ttu-id="d9679-189">2</span><span class="sxs-lookup"><span data-stu-id="d9679-189">2</span></span>|  
|<span data-ttu-id="d9679-190">3</span><span class="sxs-lookup"><span data-stu-id="d9679-190">3</span></span>|  
|<span data-ttu-id="d9679-191">...</span><span class="sxs-lookup"><span data-stu-id="d9679-191">...</span></span>|  
  
 <span data-ttu-id="d9679-192">O exemplo a seguir usa o operador de extração de propriedade (.) para acessar uma propriedade de uma entidade.</span><span class="sxs-lookup"><span data-stu-id="d9679-192">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="d9679-193">Quando o operador de extração de propriedade é usado, a referência é cancelada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d9679-193">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="d9679-194">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-194">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="d9679-195">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-195">Output:</span></span>  
  
|<span data-ttu-id="d9679-196">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-196">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-197">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="d9679-197">Adjustable Race</span></span>|  
|<span data-ttu-id="d9679-198">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="d9679-198">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="d9679-199">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="d9679-199">AWC Logo Cap</span></span>|  
|<span data-ttu-id="d9679-200">...</span><span class="sxs-lookup"><span data-stu-id="d9679-200">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="d9679-201">DEREF</span><span class="sxs-lookup"><span data-stu-id="d9679-201">DEREF</span></span>  
 <span data-ttu-id="d9679-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) desreferencia um valor de referência e gera o resultado dessa desreferência.</span><span class="sxs-lookup"><span data-stu-id="d9679-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="d9679-203">Por exemplo, a seguinte consulta gera as entidades Order para cada Order no conjunto de entidades Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="d9679-203">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="d9679-204">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-204">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="d9679-205">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-205">Output:</span></span>  
  
|<span data-ttu-id="d9679-206">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-206">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-207">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="d9679-207">Adjustable Race</span></span>|  
|<span data-ttu-id="d9679-208">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="d9679-208">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="d9679-209">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="d9679-209">AWC Logo Cap</span></span>|  
|<span data-ttu-id="d9679-210">...</span><span class="sxs-lookup"><span data-stu-id="d9679-210">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="d9679-211">CREATEREF AND KEY</span><span class="sxs-lookup"><span data-stu-id="d9679-211">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="d9679-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) cria uma referência passando uma chave.</span><span class="sxs-lookup"><span data-stu-id="d9679-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="d9679-213">[CHAVE](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrai a parte da chave de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="d9679-213">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="d9679-214">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-214">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="d9679-215">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-215">Output:</span></span>  
  
|<span data-ttu-id="d9679-216">ProductID</span><span class="sxs-lookup"><span data-stu-id="d9679-216">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="d9679-217">980</span><span class="sxs-lookup"><span data-stu-id="d9679-217">980</span></span>|  
|<span data-ttu-id="d9679-218">365</span><span class="sxs-lookup"><span data-stu-id="d9679-218">365</span></span>|  
|<span data-ttu-id="d9679-219">771</span><span class="sxs-lookup"><span data-stu-id="d9679-219">771</span></span>|  
|<span data-ttu-id="d9679-220">...</span><span class="sxs-lookup"><span data-stu-id="d9679-220">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="d9679-221">Funções</span><span class="sxs-lookup"><span data-stu-id="d9679-221">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="d9679-222">Canônica</span><span class="sxs-lookup"><span data-stu-id="d9679-222">Canonical</span></span>  
 <span data-ttu-id="d9679-223">O namespace [funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) é o Edm, como em `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="d9679-223">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="d9679-224">Você não precisa especificar o namespace, a menos que outro namespace seja importado e contenha uma função com o mesmo nome de uma função canônica.</span><span class="sxs-lookup"><span data-stu-id="d9679-224">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="d9679-225">Se dois namespaces têm a mesma função, o usuário deve especificar o nome completo.</span><span class="sxs-lookup"><span data-stu-id="d9679-225">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="d9679-226">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-226">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="d9679-227">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-227">Output:</span></span>  
  
|<span data-ttu-id="d9679-228">NameLen</span><span class="sxs-lookup"><span data-stu-id="d9679-228">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="d9679-229">6</span><span class="sxs-lookup"><span data-stu-id="d9679-229">6</span></span>|  
|<span data-ttu-id="d9679-230">6</span><span class="sxs-lookup"><span data-stu-id="d9679-230">6</span></span>|  
|<span data-ttu-id="d9679-231">5</span><span class="sxs-lookup"><span data-stu-id="d9679-231">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="d9679-232">Específico do provedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="d9679-232">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="d9679-233">[Funções específicas do provedor da Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) estão no `SqlServer` namespace.</span><span class="sxs-lookup"><span data-stu-id="d9679-233">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="d9679-234">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-234">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="d9679-235">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-235">Output:</span></span>  
  
|<span data-ttu-id="d9679-236">EmailLen</span><span class="sxs-lookup"><span data-stu-id="d9679-236">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="d9679-237">27</span><span class="sxs-lookup"><span data-stu-id="d9679-237">27</span></span>|  
|<span data-ttu-id="d9679-238">27</span><span class="sxs-lookup"><span data-stu-id="d9679-238">27</span></span>|  
|<span data-ttu-id="d9679-239">26</span><span class="sxs-lookup"><span data-stu-id="d9679-239">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="d9679-240">Namespaces</span><span class="sxs-lookup"><span data-stu-id="d9679-240">Namespaces</span></span>  
 <span data-ttu-id="d9679-241">[USANDO](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Especifica namespaces usados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="d9679-241">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="d9679-242">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-242">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="d9679-243">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-243">Output:</span></span>  
  
|<span data-ttu-id="d9679-244">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-244">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-245">aa</span><span class="sxs-lookup"><span data-stu-id="d9679-245">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="d9679-246">Paginação</span><span class="sxs-lookup"><span data-stu-id="d9679-246">Paging</span></span>  
 <span data-ttu-id="d9679-247">Paginação pode ser expressa declarando uma [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas para o [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="d9679-247">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="d9679-248">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-248">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="d9679-249">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-249">Output:</span></span>  
  
|<span data-ttu-id="d9679-250">ID</span><span class="sxs-lookup"><span data-stu-id="d9679-250">ID</span></span>|<span data-ttu-id="d9679-251">Nome</span><span class="sxs-lookup"><span data-stu-id="d9679-251">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="d9679-252">10</span><span class="sxs-lookup"><span data-stu-id="d9679-252">10</span></span>|<span data-ttu-id="d9679-253">Adina</span><span class="sxs-lookup"><span data-stu-id="d9679-253">Adina</span></span>|  
|<span data-ttu-id="d9679-254">11</span><span class="sxs-lookup"><span data-stu-id="d9679-254">11</span></span>|<span data-ttu-id="d9679-255">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="d9679-255">Agcaoili</span></span>|  
|<span data-ttu-id="d9679-256">12</span><span class="sxs-lookup"><span data-stu-id="d9679-256">12</span></span>|<span data-ttu-id="d9679-257">Aguilar</span><span class="sxs-lookup"><span data-stu-id="d9679-257">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="d9679-258">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="d9679-258">Grouping</span></span>  
 <span data-ttu-id="d9679-259">[Agrupar por](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Especifica os grupos nos quais os objetos retornados por uma consulta ([selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expressão devem ser colocados.</span><span class="sxs-lookup"><span data-stu-id="d9679-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="d9679-260">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-260">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="d9679-261">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-261">Output:</span></span>  
  
|<span data-ttu-id="d9679-262">name</span><span class="sxs-lookup"><span data-stu-id="d9679-262">name</span></span>|  
|----------|  
|<span data-ttu-id="d9679-263">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="d9679-263">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="d9679-264">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="d9679-264">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="d9679-265">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="d9679-265">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="d9679-266">...</span><span class="sxs-lookup"><span data-stu-id="d9679-266">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="d9679-267">Navegação</span><span class="sxs-lookup"><span data-stu-id="d9679-267">Navigation</span></span>  
 <span data-ttu-id="d9679-268">O operador de navegação de relação permite que você navegue na relação de uma entidade (from end) para outra (to end).</span><span class="sxs-lookup"><span data-stu-id="d9679-268">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="d9679-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) usa o tipo de relação qualificado como \<namespace >.\< nome do tipo de relação >.</span><span class="sxs-lookup"><span data-stu-id="d9679-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="d9679-270">Navegue retorna Ref\<T > se a cardinalidade de to end é 1.</span><span class="sxs-lookup"><span data-stu-id="d9679-270">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="d9679-271">Se a cardinalidade de to end for n, a coleção < Ref\<T >> será retornado.</span><span class="sxs-lookup"><span data-stu-id="d9679-271">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="d9679-272">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-272">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="d9679-273">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-273">Output:</span></span>  
  
|<span data-ttu-id="d9679-274">AddressID</span><span class="sxs-lookup"><span data-stu-id="d9679-274">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="d9679-275">1</span><span class="sxs-lookup"><span data-stu-id="d9679-275">1</span></span>|  
|<span data-ttu-id="d9679-276">2</span><span class="sxs-lookup"><span data-stu-id="d9679-276">2</span></span>|  
|<span data-ttu-id="d9679-277">3</span><span class="sxs-lookup"><span data-stu-id="d9679-277">3</span></span>|  
|<span data-ttu-id="d9679-278">...</span><span class="sxs-lookup"><span data-stu-id="d9679-278">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="d9679-279">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="d9679-279">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="d9679-280">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="d9679-280">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="d9679-281">fornece a cláusula SELECT VALUE para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="d9679-281">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="d9679-282">Somente um item pode ser especificado em uma cláusula SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="d9679-282">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="d9679-283">Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula SELECT e pode de uma coleção da forma desejada ser gerada, por exemplo: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="d9679-283">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="d9679-284">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-284">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="d9679-285">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-285">Output:</span></span>  
  
|<span data-ttu-id="d9679-286">Nome</span><span class="sxs-lookup"><span data-stu-id="d9679-286">Name</span></span>|  
|----------|  
|<span data-ttu-id="d9679-287">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="d9679-287">Adjustable Race</span></span>|  
|<span data-ttu-id="d9679-288">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="d9679-288">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="d9679-289">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="d9679-289">AWC Logo Cap</span></span>|  
|<span data-ttu-id="d9679-290">...</span><span class="sxs-lookup"><span data-stu-id="d9679-290">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="d9679-291">SELECT</span><span class="sxs-lookup"><span data-stu-id="d9679-291">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="d9679-292">também fornece o construtor de linhas para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="d9679-292">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="d9679-293">SELECT utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos; por exemplo: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="d9679-293">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="d9679-294">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-294">Example:</span></span>  
  
 <span data-ttu-id="d9679-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="d9679-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="d9679-296">Nome</span><span class="sxs-lookup"><span data-stu-id="d9679-296">Name</span></span>|<span data-ttu-id="d9679-297">ProductID</span><span class="sxs-lookup"><span data-stu-id="d9679-297">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="d9679-298">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="d9679-298">Adjustable Race</span></span>|<span data-ttu-id="d9679-299">1</span><span class="sxs-lookup"><span data-stu-id="d9679-299">1</span></span>|  
|<span data-ttu-id="d9679-300">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="d9679-300">All-Purpose Bike Stand</span></span>|<span data-ttu-id="d9679-301">879</span><span class="sxs-lookup"><span data-stu-id="d9679-301">879</span></span>|  
|<span data-ttu-id="d9679-302">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="d9679-302">AWC Logo Cap</span></span>|<span data-ttu-id="d9679-303">712</span><span class="sxs-lookup"><span data-stu-id="d9679-303">712</span></span>|  
|<span data-ttu-id="d9679-304">...</span><span class="sxs-lookup"><span data-stu-id="d9679-304">...</span></span>|<span data-ttu-id="d9679-305">...</span><span class="sxs-lookup"><span data-stu-id="d9679-305">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="d9679-306">CASE EXPRESSION</span><span class="sxs-lookup"><span data-stu-id="d9679-306">CASE EXPRESSION</span></span>  
 <span data-ttu-id="d9679-307">O [caso a expressão](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) avalia um conjunto de expressões Boolianas para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="d9679-307">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="d9679-308">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="d9679-308">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="d9679-309">Saída:</span><span class="sxs-lookup"><span data-stu-id="d9679-309">Output:</span></span>  
  
|<span data-ttu-id="d9679-310">Valor</span><span class="sxs-lookup"><span data-stu-id="d9679-310">Value</span></span>|  
|-----------|  
|<span data-ttu-id="d9679-311">TRUE</span><span class="sxs-lookup"><span data-stu-id="d9679-311">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9679-312">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9679-312">See also</span></span>

- [<span data-ttu-id="d9679-313">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9679-313">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="d9679-314">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9679-314">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
