---
title: Referência rápida de Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833871"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="e05bb-102">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e05bb-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="e05bb-103">Este tópico fornece uma referência rápida às consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e05bb-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="e05bb-104">As consultas neste tópico se baseiam no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e05bb-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="e05bb-105">{1&gt;Literais&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="e05bb-106">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e05bb-106">String</span></span>  
 <span data-ttu-id="e05bb-107">Há literais de cadeia de caracteres Unicode e não Unicode.</span><span class="sxs-lookup"><span data-stu-id="e05bb-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="e05bb-108">As cadeias de caracteres Unicode são precedidas por N. Por exemplo, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="e05bb-109">Este é um exemplo de um literal de cadeia de caracteres não Unicode:</span><span class="sxs-lookup"><span data-stu-id="e05bb-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="e05bb-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-110">Output:</span></span>  
  
|<span data-ttu-id="e05bb-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-112">hello</span><span class="sxs-lookup"><span data-stu-id="e05bb-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="e05bb-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="e05bb-113">DateTime</span></span>  
 <span data-ttu-id="e05bb-114">Em literais DateTime, as partes de data e hora são obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="e05bb-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="e05bb-115">Não há valor padrão.</span><span class="sxs-lookup"><span data-stu-id="e05bb-115">There are no default values.</span></span>  
  
 <span data-ttu-id="e05bb-116">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="e05bb-117">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-117">Output:</span></span>  
  
|<span data-ttu-id="e05bb-118">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="e05bb-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="e05bb-120">Inteiro</span><span class="sxs-lookup"><span data-stu-id="e05bb-120">Integer</span></span>  
 <span data-ttu-id="e05bb-121">Literais inteiros podem ser do tipo Int32 (123), UInt32 (123U), Int64 (123L) e UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="e05bb-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="e05bb-122">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="e05bb-123">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-123">Output:</span></span>  
  
|<span data-ttu-id="e05bb-124">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-125">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-125">1</span></span>|  
|<span data-ttu-id="e05bb-126">2</span><span class="sxs-lookup"><span data-stu-id="e05bb-126">2</span></span>|  
|<span data-ttu-id="e05bb-127">3</span><span class="sxs-lookup"><span data-stu-id="e05bb-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="e05bb-128">Outros</span><span class="sxs-lookup"><span data-stu-id="e05bb-128">Other</span></span>  
 <span data-ttu-id="e05bb-129">Outros literais com suporte do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são Guid, Binary, Float/Double, Decimal e `null`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="e05bb-130">Literais nulos em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são considerados compatíveis com cada outro tipo no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e05bb-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="e05bb-131">Construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="e05bb-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="e05bb-132">ROW</span><span class="sxs-lookup"><span data-stu-id="e05bb-132">ROW</span></span>  
 <span data-ttu-id="e05bb-133">A [linha](row-entity-sql.md) constrói um valor anônimo e estruturado de tipo (registro) como em: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="e05bb-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="e05bb-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="e05bb-135">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-135">Output:</span></span>  
  
|<span data-ttu-id="e05bb-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="e05bb-136">ProductID</span></span>|<span data-ttu-id="e05bb-137">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="e05bb-138">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-138">1</span></span>|<span data-ttu-id="e05bb-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="e05bb-139">Adjustable Race</span></span>|  
|<span data-ttu-id="e05bb-140">879</span><span class="sxs-lookup"><span data-stu-id="e05bb-140">879</span></span>|<span data-ttu-id="e05bb-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="e05bb-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e05bb-142">712</span><span class="sxs-lookup"><span data-stu-id="e05bb-142">712</span></span>|<span data-ttu-id="e05bb-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="e05bb-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e05bb-144">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-144">...</span></span>|<span data-ttu-id="e05bb-145">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="e05bb-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="e05bb-146">MULTISET</span></span>  
 <span data-ttu-id="e05bb-147">As coleções de [vários](multiset-entity-sql.md) conjuntos de construções, como:</span><span class="sxs-lookup"><span data-stu-id="e05bb-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="e05bb-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="e05bb-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="e05bb-149">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="e05bb-150">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-150">Output:</span></span>  
  
|<span data-ttu-id="e05bb-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="e05bb-151">ProductID</span></span>|<span data-ttu-id="e05bb-152">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-152">Name</span></span>|<span data-ttu-id="e05bb-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="e05bb-153">ProductNumber</span></span>|<span data-ttu-id="e05bb-154">…</span><span class="sxs-lookup"><span data-stu-id="e05bb-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="e05bb-155">842</span><span class="sxs-lookup"><span data-stu-id="e05bb-155">842</span></span>|<span data-ttu-id="e05bb-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="e05bb-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="e05bb-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="e05bb-157">PA-T100</span></span>|<span data-ttu-id="e05bb-158">…</span><span class="sxs-lookup"><span data-stu-id="e05bb-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="e05bb-159">Object</span><span class="sxs-lookup"><span data-stu-id="e05bb-159">Object</span></span>  
 <span data-ttu-id="e05bb-160">O [Construtor de tipo nomeado](named-type-constructor-entity-sql.md) cria objetos (chamados) definidos pelo usuário, como `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="e05bb-161">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="e05bb-162">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-162">Output:</span></span>  
  
|<span data-ttu-id="e05bb-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="e05bb-163">SalesOrderDetailID</span></span>|<span data-ttu-id="e05bb-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="e05bb-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="e05bb-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="e05bb-165">OrderQty</span></span>|<span data-ttu-id="e05bb-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="e05bb-166">ProductID</span></span>|<span data-ttu-id="e05bb-167">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="e05bb-168">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-168">1</span></span>|<span data-ttu-id="e05bb-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e05bb-169">4911-403C-98</span></span>|<span data-ttu-id="e05bb-170">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-170">1</span></span>|<span data-ttu-id="e05bb-171">776</span><span class="sxs-lookup"><span data-stu-id="e05bb-171">776</span></span>|<span data-ttu-id="e05bb-172">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-172">...</span></span>|  
|<span data-ttu-id="e05bb-173">2</span><span class="sxs-lookup"><span data-stu-id="e05bb-173">2</span></span>|<span data-ttu-id="e05bb-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="e05bb-174">4911-403C-98</span></span>|<span data-ttu-id="e05bb-175">3</span><span class="sxs-lookup"><span data-stu-id="e05bb-175">3</span></span>|<span data-ttu-id="e05bb-176">777</span><span class="sxs-lookup"><span data-stu-id="e05bb-176">777</span></span>|<span data-ttu-id="e05bb-177">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-177">...</span></span>|  
|<span data-ttu-id="e05bb-178">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-178">...</span></span>|<span data-ttu-id="e05bb-179">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-179">...</span></span>|<span data-ttu-id="e05bb-180">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-180">...</span></span>|<span data-ttu-id="e05bb-181">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-181">...</span></span>|<span data-ttu-id="e05bb-182">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="e05bb-183">Referências</span><span class="sxs-lookup"><span data-stu-id="e05bb-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e05bb-184">REF</span><span class="sxs-lookup"><span data-stu-id="e05bb-184">REF</span></span>  
 <span data-ttu-id="e05bb-185">[Ref](ref-entity-sql.md) cria uma referência a uma instância de tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="e05bb-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="e05bb-186">Por exemplo, a seguinte consulta retorna referências para cada entidade Order no conjunto de entidades Orders:</span><span class="sxs-lookup"><span data-stu-id="e05bb-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="e05bb-187">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-187">Output:</span></span>  
  
|<span data-ttu-id="e05bb-188">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-189">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-189">1</span></span>|  
|<span data-ttu-id="e05bb-190">2</span><span class="sxs-lookup"><span data-stu-id="e05bb-190">2</span></span>|  
|<span data-ttu-id="e05bb-191">3</span><span class="sxs-lookup"><span data-stu-id="e05bb-191">3</span></span>|  
|<span data-ttu-id="e05bb-192">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-192">...</span></span>|  
  
 <span data-ttu-id="e05bb-193">O exemplo a seguir usa o operador de extração de propriedade (.) para acessar uma propriedade de uma entidade.</span><span class="sxs-lookup"><span data-stu-id="e05bb-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="e05bb-194">Quando o operador de extração de propriedade é usado, a referência é cancelada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e05bb-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="e05bb-195">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="e05bb-196">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-196">Output:</span></span>  
  
|<span data-ttu-id="e05bb-197">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="e05bb-198">Adjustable Race</span></span>|  
|<span data-ttu-id="e05bb-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="e05bb-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e05bb-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="e05bb-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e05bb-201">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="e05bb-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="e05bb-202">DEREF</span></span>  
 <span data-ttu-id="e05bb-203">[DEREF](deref-entity-sql.md) faz a referência de um valor de referência e produz o resultado dessa desreferência.</span><span class="sxs-lookup"><span data-stu-id="e05bb-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="e05bb-204">Por exemplo, a seguinte consulta gera as entidades Order para cada Order no conjunto de entidades Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="e05bb-205">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="e05bb-206">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-206">Output:</span></span>  
  
|<span data-ttu-id="e05bb-207">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="e05bb-208">Adjustable Race</span></span>|  
|<span data-ttu-id="e05bb-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="e05bb-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e05bb-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="e05bb-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e05bb-211">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="e05bb-212">CREATEREF AND KEY</span><span class="sxs-lookup"><span data-stu-id="e05bb-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="e05bb-213">[CREATEREF](createref-entity-sql.md) cria uma referência passando uma chave.</span><span class="sxs-lookup"><span data-stu-id="e05bb-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="e05bb-214">A [chave](key-entity-sql.md) extrai a parte de chave de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="e05bb-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="e05bb-215">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="e05bb-216">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-216">Output:</span></span>  
  
|<span data-ttu-id="e05bb-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="e05bb-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="e05bb-218">980</span><span class="sxs-lookup"><span data-stu-id="e05bb-218">980</span></span>|  
|<span data-ttu-id="e05bb-219">365</span><span class="sxs-lookup"><span data-stu-id="e05bb-219">365</span></span>|  
|<span data-ttu-id="e05bb-220">771</span><span class="sxs-lookup"><span data-stu-id="e05bb-220">771</span></span>|  
|<span data-ttu-id="e05bb-221">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="e05bb-222">{1&gt;Funções&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="e05bb-223">Canônica</span><span class="sxs-lookup"><span data-stu-id="e05bb-223">Canonical</span></span>  
 <span data-ttu-id="e05bb-224">O namespace para [funções canônicas](canonical-functions.md) é EDM, como em `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="e05bb-225">Você não precisa especificar o namespace, a menos que outro namespace seja importado e contenha uma função com o mesmo nome de uma função canônica.</span><span class="sxs-lookup"><span data-stu-id="e05bb-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="e05bb-226">Se dois namespaces têm a mesma função, o usuário deve especificar o nome completo.</span><span class="sxs-lookup"><span data-stu-id="e05bb-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="e05bb-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e05bb-228">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-228">Output:</span></span>  
  
|<span data-ttu-id="e05bb-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="e05bb-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="e05bb-230">6</span><span class="sxs-lookup"><span data-stu-id="e05bb-230">6</span></span>|  
|<span data-ttu-id="e05bb-231">6</span><span class="sxs-lookup"><span data-stu-id="e05bb-231">6</span></span>|  
|<span data-ttu-id="e05bb-232">5</span><span class="sxs-lookup"><span data-stu-id="e05bb-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="e05bb-233">Específico do provedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="e05bb-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="e05bb-234">As [funções específicas do provedor da Microsoft](../sqlclient-for-ef-functions.md) estão no namespace `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="e05bb-235">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="e05bb-236">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-236">Output:</span></span>  
  
|<span data-ttu-id="e05bb-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="e05bb-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="e05bb-238">27</span><span class="sxs-lookup"><span data-stu-id="e05bb-238">27</span></span>|  
|<span data-ttu-id="e05bb-239">27</span><span class="sxs-lookup"><span data-stu-id="e05bb-239">27</span></span>|  
|<span data-ttu-id="e05bb-240">26</span><span class="sxs-lookup"><span data-stu-id="e05bb-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="e05bb-241">{1&gt;Namespaces&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-241">Namespaces</span></span>  
 <span data-ttu-id="e05bb-242">O [uso](using-entity-sql.md) de especifica namespaces usados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="e05bb-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="e05bb-243">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="e05bb-244">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-244">Output:</span></span>  
  
|<span data-ttu-id="e05bb-245">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-246">aa</span><span class="sxs-lookup"><span data-stu-id="e05bb-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="e05bb-247">Paginação</span><span class="sxs-lookup"><span data-stu-id="e05bb-247">Paging</span></span>  
 <span data-ttu-id="e05bb-248">A paginação pode ser expressa declarando-se uma subcláusula [Skip](skip-entity-sql.md) e [Limit](limit-entity-sql.md) com a cláusula [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="e05bb-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="e05bb-249">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="e05bb-250">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-250">Output:</span></span>  
  
|<span data-ttu-id="e05bb-251">ID</span><span class="sxs-lookup"><span data-stu-id="e05bb-251">ID</span></span>|<span data-ttu-id="e05bb-252">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="e05bb-253">10</span><span class="sxs-lookup"><span data-stu-id="e05bb-253">10</span></span>|<span data-ttu-id="e05bb-254">Adina</span><span class="sxs-lookup"><span data-stu-id="e05bb-254">Adina</span></span>|  
|<span data-ttu-id="e05bb-255">11</span><span class="sxs-lookup"><span data-stu-id="e05bb-255">11</span></span>|<span data-ttu-id="e05bb-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="e05bb-256">Agcaoili</span></span>|  
|<span data-ttu-id="e05bb-257">12</span><span class="sxs-lookup"><span data-stu-id="e05bb-257">12</span></span>|<span data-ttu-id="e05bb-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="e05bb-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="e05bb-259">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="e05bb-259">Grouping</span></span>  
 <span data-ttu-id="e05bb-260">O [agrupamento](group-by-entity-sql.md) especifica os grupos nos quais os objetos retornados por uma expressão de consulta ([Select](select-entity-sql.md)) devem ser colocados.</span><span class="sxs-lookup"><span data-stu-id="e05bb-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="e05bb-261">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="e05bb-262">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-262">Output:</span></span>  
  
|<span data-ttu-id="e05bb-263">name</span><span class="sxs-lookup"><span data-stu-id="e05bb-263">name</span></span>|  
|----------|  
|<span data-ttu-id="e05bb-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="e05bb-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e05bb-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="e05bb-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e05bb-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="e05bb-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="e05bb-267">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="e05bb-268">Navegação</span><span class="sxs-lookup"><span data-stu-id="e05bb-268">Navigation</span></span>  
 <span data-ttu-id="e05bb-269">O operador de navegação de relação permite que você navegue na relação de uma entidade (from end) para outra (to end).</span><span class="sxs-lookup"><span data-stu-id="e05bb-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="e05bb-270">A [navegação](navigate-entity-sql.md) usa o tipo de relação qualificado como \<namespace >.\<nome do tipo de relação >.</span><span class="sxs-lookup"><span data-stu-id="e05bb-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="e05bb-271">Navigate retorna REF\<T > se a cardinalidade da extremidade to for 1.</span><span class="sxs-lookup"><span data-stu-id="e05bb-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="e05bb-272">Se a cardinalidade do to end for n, a coleção < ref\<T > > será retornada.</span><span class="sxs-lookup"><span data-stu-id="e05bb-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="e05bb-273">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="e05bb-274">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-274">Output:</span></span>  
  
|<span data-ttu-id="e05bb-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="e05bb-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="e05bb-276">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-276">1</span></span>|  
|<span data-ttu-id="e05bb-277">2</span><span class="sxs-lookup"><span data-stu-id="e05bb-277">2</span></span>|  
|<span data-ttu-id="e05bb-278">3</span><span class="sxs-lookup"><span data-stu-id="e05bb-278">3</span></span>|  
|<span data-ttu-id="e05bb-279">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="e05bb-280">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="e05bb-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="e05bb-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="e05bb-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e05bb-282">fornece a cláusula SELECT VALUE para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="e05bb-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="e05bb-283">Somente um item pode ser especificado em uma cláusula SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="e05bb-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="e05bb-284">Quando tal cláusula é usada, nenhum wrapper de linha é construído em volta dos itens na cláusula SELECT e uma coleção da forma desejada pode ser produzida, por exemplo: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="e05bb-285">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="e05bb-286">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-286">Output:</span></span>  
  
|<span data-ttu-id="e05bb-287">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="e05bb-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="e05bb-288">Adjustable Race</span></span>|  
|<span data-ttu-id="e05bb-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="e05bb-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="e05bb-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="e05bb-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="e05bb-291">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="e05bb-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="e05bb-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="e05bb-293">também fornece o Construtor Row para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="e05bb-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="e05bb-294">SELECT utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos; por exemplo: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="e05bb-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="e05bb-295">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-295">Example:</span></span>  
  
 <span data-ttu-id="e05bb-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="e05bb-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="e05bb-297">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e05bb-297">Name</span></span>|<span data-ttu-id="e05bb-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="e05bb-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="e05bb-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="e05bb-299">Adjustable Race</span></span>|<span data-ttu-id="e05bb-300">1</span><span class="sxs-lookup"><span data-stu-id="e05bb-300">1</span></span>|  
|<span data-ttu-id="e05bb-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="e05bb-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="e05bb-302">879</span><span class="sxs-lookup"><span data-stu-id="e05bb-302">879</span></span>|  
|<span data-ttu-id="e05bb-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="e05bb-303">AWC Logo Cap</span></span>|<span data-ttu-id="e05bb-304">712</span><span class="sxs-lookup"><span data-stu-id="e05bb-304">712</span></span>|  
|<span data-ttu-id="e05bb-305">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-305">...</span></span>|<span data-ttu-id="e05bb-306">...</span><span class="sxs-lookup"><span data-stu-id="e05bb-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="e05bb-307">CASE EXPRESSION</span><span class="sxs-lookup"><span data-stu-id="e05bb-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="e05bb-308">A [expressão CASE](case-entity-sql.md) avalia um conjunto de expressões boolianas para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="e05bb-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="e05bb-309">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="e05bb-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="e05bb-310">Saída:</span><span class="sxs-lookup"><span data-stu-id="e05bb-310">Output:</span></span>  
  
|<span data-ttu-id="e05bb-311">Valor</span><span class="sxs-lookup"><span data-stu-id="e05bb-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="e05bb-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="e05bb-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e05bb-313">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e05bb-313">See also</span></span>

- [<span data-ttu-id="e05bb-314">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e05bb-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e05bb-315">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e05bb-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
