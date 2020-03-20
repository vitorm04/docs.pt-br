---
title: Referência rápida de Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150344"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="b18df-102">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b18df-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="b18df-103">Este tópico fornece uma referência rápida às consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b18df-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="b18df-104">As consultas deste tópico se baseiam no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b18df-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="b18df-105">Literais</span><span class="sxs-lookup"><span data-stu-id="b18df-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="b18df-106">String</span><span class="sxs-lookup"><span data-stu-id="b18df-106">String</span></span>  
 <span data-ttu-id="b18df-107">Há literais de cadeia de caracteres Unicode e não Unicode.</span><span class="sxs-lookup"><span data-stu-id="b18df-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="b18df-108">As seqüências unicode são preparadas com N. Por exemplo, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="b18df-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="b18df-109">Este é um exemplo de um literal de cadeia de caracteres não Unicode:</span><span class="sxs-lookup"><span data-stu-id="b18df-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="b18df-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-110">Output:</span></span>  
  
|<span data-ttu-id="b18df-111">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-112">hello</span><span class="sxs-lookup"><span data-stu-id="b18df-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="b18df-113">Datetime</span><span class="sxs-lookup"><span data-stu-id="b18df-113">DateTime</span></span>  
 <span data-ttu-id="b18df-114">Em literais DateTime, as partes de data e hora são obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="b18df-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="b18df-115">Não há valores padrão.</span><span class="sxs-lookup"><span data-stu-id="b18df-115">There are no default values.</span></span>  
  
 <span data-ttu-id="b18df-116">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="b18df-117">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-117">Output:</span></span>  
  
|<span data-ttu-id="b18df-118">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="b18df-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="b18df-120">Integer</span><span class="sxs-lookup"><span data-stu-id="b18df-120">Integer</span></span>  
 <span data-ttu-id="b18df-121">Literais inteiros podem ser do tipo Int32 (123), UInt32 (123U), Int64 (123L) e UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="b18df-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="b18df-122">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="b18df-123">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-123">Output:</span></span>  
  
|<span data-ttu-id="b18df-124">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-125">1</span><span class="sxs-lookup"><span data-stu-id="b18df-125">1</span></span>|  
|<span data-ttu-id="b18df-126">2</span><span class="sxs-lookup"><span data-stu-id="b18df-126">2</span></span>|  
|<span data-ttu-id="b18df-127">3</span><span class="sxs-lookup"><span data-stu-id="b18df-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="b18df-128">Outros</span><span class="sxs-lookup"><span data-stu-id="b18df-128">Other</span></span>  
 <span data-ttu-id="b18df-129">Outros literais com suporte do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são Guid, Binary, Float/Double, Decimal e `null`.</span><span class="sxs-lookup"><span data-stu-id="b18df-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="b18df-130">Literais nulos em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são considerados compatíveis com cada outro tipo no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="b18df-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="b18df-131">Construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="b18df-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="b18df-132">ROW</span><span class="sxs-lookup"><span data-stu-id="b18df-132">ROW</span></span>  
 <span data-ttu-id="b18df-133">[Row](row-entity-sql.md) constrói um valor anônimo, estruturalmente digitado (registro) como em:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="b18df-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="b18df-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="b18df-135">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-135">Output:</span></span>  
  
|<span data-ttu-id="b18df-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="b18df-136">ProductID</span></span>|<span data-ttu-id="b18df-137">Nome</span><span class="sxs-lookup"><span data-stu-id="b18df-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="b18df-138">1</span><span class="sxs-lookup"><span data-stu-id="b18df-138">1</span></span>|<span data-ttu-id="b18df-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b18df-139">Adjustable Race</span></span>|  
|<span data-ttu-id="b18df-140">879</span><span class="sxs-lookup"><span data-stu-id="b18df-140">879</span></span>|<span data-ttu-id="b18df-141">Suporte de bicicleta multifuncional</span><span class="sxs-lookup"><span data-stu-id="b18df-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b18df-142">712</span><span class="sxs-lookup"><span data-stu-id="b18df-142">712</span></span>|<span data-ttu-id="b18df-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b18df-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b18df-144">...</span><span class="sxs-lookup"><span data-stu-id="b18df-144">...</span></span>|<span data-ttu-id="b18df-145">...</span><span class="sxs-lookup"><span data-stu-id="b18df-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="b18df-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="b18df-146">MULTISET</span></span>  
 <span data-ttu-id="b18df-147">[Multiset](multiset-entity-sql.md) constrói coleções, tais como:</span><span class="sxs-lookup"><span data-stu-id="b18df-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="b18df-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="b18df-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="b18df-149">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="b18df-150">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-150">Output:</span></span>  
  
|<span data-ttu-id="b18df-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="b18df-151">ProductID</span></span>|<span data-ttu-id="b18df-152">Nome</span><span class="sxs-lookup"><span data-stu-id="b18df-152">Name</span></span>|<span data-ttu-id="b18df-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="b18df-153">ProductNumber</span></span>|<span data-ttu-id="b18df-154">…</span><span class="sxs-lookup"><span data-stu-id="b18df-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="b18df-155">842</span><span class="sxs-lookup"><span data-stu-id="b18df-155">842</span></span>|<span data-ttu-id="b18df-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="b18df-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="b18df-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="b18df-157">PA-T100</span></span>|<span data-ttu-id="b18df-158">…</span><span class="sxs-lookup"><span data-stu-id="b18df-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="b18df-159">Objeto</span><span class="sxs-lookup"><span data-stu-id="b18df-159">Object</span></span>  
 <span data-ttu-id="b18df-160">[O Tipo Construtor](named-type-constructor-entity-sql.md) denominado construções (nomeado) `person("abc", 12)`objetos definidos pelo usuário, tais como .</span><span class="sxs-lookup"><span data-stu-id="b18df-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="b18df-161">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="b18df-162">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-162">Output:</span></span>  
  
|<span data-ttu-id="b18df-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="b18df-163">SalesOrderDetailID</span></span>|<span data-ttu-id="b18df-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="b18df-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="b18df-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="b18df-165">OrderQty</span></span>|<span data-ttu-id="b18df-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="b18df-166">ProductID</span></span>|<span data-ttu-id="b18df-167">...</span><span class="sxs-lookup"><span data-stu-id="b18df-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="b18df-168">1</span><span class="sxs-lookup"><span data-stu-id="b18df-168">1</span></span>|<span data-ttu-id="b18df-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b18df-169">4911-403C-98</span></span>|<span data-ttu-id="b18df-170">1</span><span class="sxs-lookup"><span data-stu-id="b18df-170">1</span></span>|<span data-ttu-id="b18df-171">776</span><span class="sxs-lookup"><span data-stu-id="b18df-171">776</span></span>|<span data-ttu-id="b18df-172">...</span><span class="sxs-lookup"><span data-stu-id="b18df-172">...</span></span>|  
|<span data-ttu-id="b18df-173">2</span><span class="sxs-lookup"><span data-stu-id="b18df-173">2</span></span>|<span data-ttu-id="b18df-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b18df-174">4911-403C-98</span></span>|<span data-ttu-id="b18df-175">3</span><span class="sxs-lookup"><span data-stu-id="b18df-175">3</span></span>|<span data-ttu-id="b18df-176">777</span><span class="sxs-lookup"><span data-stu-id="b18df-176">777</span></span>|<span data-ttu-id="b18df-177">...</span><span class="sxs-lookup"><span data-stu-id="b18df-177">...</span></span>|  
|<span data-ttu-id="b18df-178">...</span><span class="sxs-lookup"><span data-stu-id="b18df-178">...</span></span>|<span data-ttu-id="b18df-179">...</span><span class="sxs-lookup"><span data-stu-id="b18df-179">...</span></span>|<span data-ttu-id="b18df-180">...</span><span class="sxs-lookup"><span data-stu-id="b18df-180">...</span></span>|<span data-ttu-id="b18df-181">...</span><span class="sxs-lookup"><span data-stu-id="b18df-181">...</span></span>|<span data-ttu-id="b18df-182">...</span><span class="sxs-lookup"><span data-stu-id="b18df-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="b18df-183">Referências</span><span class="sxs-lookup"><span data-stu-id="b18df-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b18df-184">REF</span><span class="sxs-lookup"><span data-stu-id="b18df-184">REF</span></span>  
 <span data-ttu-id="b18df-185">[O REF](ref-entity-sql.md) cria uma referência a uma instância de tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="b18df-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="b18df-186">Por exemplo, a seguinte consulta retorna referências para cada entidade Order no conjunto de entidades Orders:</span><span class="sxs-lookup"><span data-stu-id="b18df-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="b18df-187">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-187">Output:</span></span>  
  
|<span data-ttu-id="b18df-188">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-189">1</span><span class="sxs-lookup"><span data-stu-id="b18df-189">1</span></span>|  
|<span data-ttu-id="b18df-190">2</span><span class="sxs-lookup"><span data-stu-id="b18df-190">2</span></span>|  
|<span data-ttu-id="b18df-191">3</span><span class="sxs-lookup"><span data-stu-id="b18df-191">3</span></span>|  
|<span data-ttu-id="b18df-192">...</span><span class="sxs-lookup"><span data-stu-id="b18df-192">...</span></span>|  
  
 <span data-ttu-id="b18df-193">O exemplo a seguir usa o operador de extração de propriedade (.) para acessar uma propriedade de uma entidade.</span><span class="sxs-lookup"><span data-stu-id="b18df-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="b18df-194">Quando o operador de extração de propriedade é usado, a referência é cancelada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b18df-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="b18df-195">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b18df-196">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-196">Output:</span></span>  
  
|<span data-ttu-id="b18df-197">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b18df-198">Adjustable Race</span></span>|  
|<span data-ttu-id="b18df-199">Suporte de bicicleta multifuncional</span><span class="sxs-lookup"><span data-stu-id="b18df-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b18df-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b18df-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b18df-201">...</span><span class="sxs-lookup"><span data-stu-id="b18df-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="b18df-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="b18df-202">DEREF</span></span>  
 <span data-ttu-id="b18df-203">[O DEREF](deref-entity-sql.md) defaz referência a um valor de referência e produz o resultado dessa dereferência.</span><span class="sxs-lookup"><span data-stu-id="b18df-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="b18df-204">Por exemplo, a seguinte consulta gera as entidades Order para cada Order no conjunto de entidades Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="b18df-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="b18df-205">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b18df-206">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-206">Output:</span></span>  
  
|<span data-ttu-id="b18df-207">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b18df-208">Adjustable Race</span></span>|  
|<span data-ttu-id="b18df-209">Suporte de bicicleta multifuncional</span><span class="sxs-lookup"><span data-stu-id="b18df-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b18df-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b18df-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b18df-211">...</span><span class="sxs-lookup"><span data-stu-id="b18df-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="b18df-212">CREATEREF AND KEY</span><span class="sxs-lookup"><span data-stu-id="b18df-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="b18df-213">[CREATEREF](createref-entity-sql.md) cria uma referência passando uma chave.</span><span class="sxs-lookup"><span data-stu-id="b18df-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="b18df-214">[Key](key-entity-sql.md) extrai a parte-chave de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="b18df-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="b18df-215">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b18df-216">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-216">Output:</span></span>  
  
|<span data-ttu-id="b18df-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="b18df-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="b18df-218">980</span><span class="sxs-lookup"><span data-stu-id="b18df-218">980</span></span>|  
|<span data-ttu-id="b18df-219">365</span><span class="sxs-lookup"><span data-stu-id="b18df-219">365</span></span>|  
|<span data-ttu-id="b18df-220">771</span><span class="sxs-lookup"><span data-stu-id="b18df-220">771</span></span>|  
|<span data-ttu-id="b18df-221">...</span><span class="sxs-lookup"><span data-stu-id="b18df-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="b18df-222">Funções</span><span class="sxs-lookup"><span data-stu-id="b18df-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="b18df-223">Canônico</span><span class="sxs-lookup"><span data-stu-id="b18df-223">Canonical</span></span>  
 <span data-ttu-id="b18df-224">O namespace para [funções canônicas](canonical-functions.md) é `Edm.Length("string")`Edm, como em .</span><span class="sxs-lookup"><span data-stu-id="b18df-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="b18df-225">Você não precisa especificar o namespace, a menos que outro namespace seja importado e contenha uma função com o mesmo nome de uma função canônica.</span><span class="sxs-lookup"><span data-stu-id="b18df-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="b18df-226">Se dois namespaces têm a mesma função, o usuário deve especificar o nome completo.</span><span class="sxs-lookup"><span data-stu-id="b18df-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="b18df-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b18df-228">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-228">Output:</span></span>  
  
|<span data-ttu-id="b18df-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="b18df-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="b18df-230">6</span><span class="sxs-lookup"><span data-stu-id="b18df-230">6</span></span>|  
|<span data-ttu-id="b18df-231">6</span><span class="sxs-lookup"><span data-stu-id="b18df-231">6</span></span>|  
|<span data-ttu-id="b18df-232">5</span><span class="sxs-lookup"><span data-stu-id="b18df-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="b18df-233">Específico do provedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="b18df-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="b18df-234">[As funções específicas do](../sqlclient-for-ef-functions.md) `SqlServer` provedor da Microsoft estão no namespace.</span><span class="sxs-lookup"><span data-stu-id="b18df-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="b18df-235">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b18df-236">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-236">Output:</span></span>  
  
|<span data-ttu-id="b18df-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="b18df-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="b18df-238">27</span><span class="sxs-lookup"><span data-stu-id="b18df-238">27</span></span>|  
|<span data-ttu-id="b18df-239">27</span><span class="sxs-lookup"><span data-stu-id="b18df-239">27</span></span>|  
|<span data-ttu-id="b18df-240">26</span><span class="sxs-lookup"><span data-stu-id="b18df-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="b18df-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="b18df-241">Namespaces</span></span>  
 <span data-ttu-id="b18df-242">[O USO](using-entity-sql.md) especifica os namespaces usados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="b18df-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="b18df-243">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="b18df-244">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-244">Output:</span></span>  
  
|<span data-ttu-id="b18df-245">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-246">aa</span><span class="sxs-lookup"><span data-stu-id="b18df-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="b18df-247">Paginamento</span><span class="sxs-lookup"><span data-stu-id="b18df-247">Paging</span></span>  
 <span data-ttu-id="b18df-248">A paginação pode ser expressa declarando uma subcláusula [SKIP](skip-entity-sql.md) e [LIMIT](limit-entity-sql.md) à cláusula [ORDER BY.](order-by-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="b18df-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="b18df-249">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="b18df-250">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-250">Output:</span></span>  
  
|<span data-ttu-id="b18df-251">ID</span><span class="sxs-lookup"><span data-stu-id="b18df-251">ID</span></span>|<span data-ttu-id="b18df-252">Nome</span><span class="sxs-lookup"><span data-stu-id="b18df-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="b18df-253">10</span><span class="sxs-lookup"><span data-stu-id="b18df-253">10</span></span>|<span data-ttu-id="b18df-254">Adina</span><span class="sxs-lookup"><span data-stu-id="b18df-254">Adina</span></span>|  
|<span data-ttu-id="b18df-255">11</span><span class="sxs-lookup"><span data-stu-id="b18df-255">11</span></span>|<span data-ttu-id="b18df-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="b18df-256">Agcaoili</span></span>|  
|<span data-ttu-id="b18df-257">12</span><span class="sxs-lookup"><span data-stu-id="b18df-257">12</span></span>|<span data-ttu-id="b18df-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="b18df-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="b18df-259">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="b18df-259">Grouping</span></span>  
 <span data-ttu-id="b18df-260">[O AGRUPAMENTO POR](group-by-entity-sql.md) especifica grupos nos quais os objetos retornados por uma expressão de consulta[(SELECT)](select-entity-sql.md)devem ser colocados.</span><span class="sxs-lookup"><span data-stu-id="b18df-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="b18df-261">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="b18df-262">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-262">Output:</span></span>  
  
|<span data-ttu-id="b18df-263">name</span><span class="sxs-lookup"><span data-stu-id="b18df-263">name</span></span>|  
|----------|  
|<span data-ttu-id="b18df-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b18df-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b18df-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b18df-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b18df-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b18df-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b18df-267">...</span><span class="sxs-lookup"><span data-stu-id="b18df-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="b18df-268">Navegação</span><span class="sxs-lookup"><span data-stu-id="b18df-268">Navigation</span></span>  
 <span data-ttu-id="b18df-269">O operador de navegação de relação permite que você navegue na relação de uma entidade (from end) para outra (to end).</span><span class="sxs-lookup"><span data-stu-id="b18df-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="b18df-270">[O NAVIGATE](navigate-entity-sql.md) tem o \<tipo de relacionamento qualificado como namespace>. \<nome do tipo de relacionamento>.</span><span class="sxs-lookup"><span data-stu-id="b18df-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="b18df-271">Navegar retorna\<Ref T> se a cardinalidade do fim for 1.</span><span class="sxs-lookup"><span data-stu-id="b18df-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="b18df-272">Se a cardinalidade do fim for n,\<a Coleção<Ref T>> será devolvida.</span><span class="sxs-lookup"><span data-stu-id="b18df-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="b18df-273">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="b18df-274">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-274">Output:</span></span>  
  
|<span data-ttu-id="b18df-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="b18df-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="b18df-276">1</span><span class="sxs-lookup"><span data-stu-id="b18df-276">1</span></span>|  
|<span data-ttu-id="b18df-277">2</span><span class="sxs-lookup"><span data-stu-id="b18df-277">2</span></span>|  
|<span data-ttu-id="b18df-278">3</span><span class="sxs-lookup"><span data-stu-id="b18df-278">3</span></span>|  
|<span data-ttu-id="b18df-279">...</span><span class="sxs-lookup"><span data-stu-id="b18df-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="b18df-280">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="b18df-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="b18df-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="b18df-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b18df-282">fornece a cláusula SELECT VALUE para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="b18df-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="b18df-283">Somente um item pode ser especificado em uma cláusula SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="b18df-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="b18df-284">Quando tal cláusula é usada, nenhum invólucro de linha é construído em torno dos itens da cláusula SELECT, e uma coleção da forma desejada pode ser produzida, por exemplo: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="b18df-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="b18df-285">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b18df-286">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-286">Output:</span></span>  
  
|<span data-ttu-id="b18df-287">Nome</span><span class="sxs-lookup"><span data-stu-id="b18df-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="b18df-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b18df-288">Adjustable Race</span></span>|  
|<span data-ttu-id="b18df-289">Suporte de bicicleta multifuncional</span><span class="sxs-lookup"><span data-stu-id="b18df-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b18df-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b18df-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b18df-291">...</span><span class="sxs-lookup"><span data-stu-id="b18df-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="b18df-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="b18df-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b18df-293">também fornece o construtor de linha para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="b18df-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="b18df-294">SELECT utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos; por exemplo: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="b18df-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="b18df-295">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-295">Example:</span></span>  
  
 <span data-ttu-id="b18df-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="b18df-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="b18df-297">Nome</span><span class="sxs-lookup"><span data-stu-id="b18df-297">Name</span></span>|<span data-ttu-id="b18df-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="b18df-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="b18df-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b18df-299">Adjustable Race</span></span>|<span data-ttu-id="b18df-300">1</span><span class="sxs-lookup"><span data-stu-id="b18df-300">1</span></span>|  
|<span data-ttu-id="b18df-301">Suporte de bicicleta multifuncional</span><span class="sxs-lookup"><span data-stu-id="b18df-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="b18df-302">879</span><span class="sxs-lookup"><span data-stu-id="b18df-302">879</span></span>|  
|<span data-ttu-id="b18df-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b18df-303">AWC Logo Cap</span></span>|<span data-ttu-id="b18df-304">712</span><span class="sxs-lookup"><span data-stu-id="b18df-304">712</span></span>|  
|<span data-ttu-id="b18df-305">...</span><span class="sxs-lookup"><span data-stu-id="b18df-305">...</span></span>|<span data-ttu-id="b18df-306">...</span><span class="sxs-lookup"><span data-stu-id="b18df-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="b18df-307">CASE EXPRESSION</span><span class="sxs-lookup"><span data-stu-id="b18df-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="b18df-308">A [expressão do caso](case-entity-sql.md) avalia um conjunto de expressões booleanas para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="b18df-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="b18df-309">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="b18df-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="b18df-310">Saída:</span><span class="sxs-lookup"><span data-stu-id="b18df-310">Output:</span></span>  
  
|<span data-ttu-id="b18df-311">Valor</span><span class="sxs-lookup"><span data-stu-id="b18df-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b18df-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="b18df-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b18df-313">Confira também</span><span class="sxs-lookup"><span data-stu-id="b18df-313">See also</span></span>

- [<span data-ttu-id="b18df-314">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b18df-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b18df-315">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b18df-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
