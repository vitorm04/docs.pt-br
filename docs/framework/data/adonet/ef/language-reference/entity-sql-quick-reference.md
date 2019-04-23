---
title: Referência rápida de Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207065"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="a0d49-102">Referência rápida de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a0d49-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="a0d49-103">Este tópico fornece uma referência rápida às consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0d49-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="a0d49-104">As consultas neste tópico baseiam-se no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a0d49-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="a0d49-105">Literais</span><span class="sxs-lookup"><span data-stu-id="a0d49-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="a0d49-106">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a0d49-106">String</span></span>  
 <span data-ttu-id="a0d49-107">Há literais de cadeia de caracteres Unicode e não Unicode.</span><span class="sxs-lookup"><span data-stu-id="a0d49-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="a0d49-108">Cadeias de caracteres Unicode são pré-demarcadas com N. Por exemplo, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="a0d49-109">Este é um exemplo de um literal de cadeia de caracteres não Unicode:</span><span class="sxs-lookup"><span data-stu-id="a0d49-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="a0d49-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-110">Output:</span></span>  
  
|<span data-ttu-id="a0d49-111">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-112">hello</span><span class="sxs-lookup"><span data-stu-id="a0d49-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="a0d49-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="a0d49-113">DateTime</span></span>  
 <span data-ttu-id="a0d49-114">Em literais DateTime, as partes de data e hora são obrigatórias.</span><span class="sxs-lookup"><span data-stu-id="a0d49-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="a0d49-115">Não há valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a0d49-115">There are no default values.</span></span>  
  
 <span data-ttu-id="a0d49-116">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="a0d49-117">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-117">Output:</span></span>  
  
|<span data-ttu-id="a0d49-118">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="a0d49-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="a0d49-120">Inteiro</span><span class="sxs-lookup"><span data-stu-id="a0d49-120">Integer</span></span>  
 <span data-ttu-id="a0d49-121">Literais inteiros podem ser do tipo Int32 (123), UInt32 (123U), Int64 (123L) e UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="a0d49-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="a0d49-122">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="a0d49-123">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-123">Output:</span></span>  
  
|<span data-ttu-id="a0d49-124">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-125">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-125">1</span></span>|  
|<span data-ttu-id="a0d49-126">2</span><span class="sxs-lookup"><span data-stu-id="a0d49-126">2</span></span>|  
|<span data-ttu-id="a0d49-127">3</span><span class="sxs-lookup"><span data-stu-id="a0d49-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="a0d49-128">Outros</span><span class="sxs-lookup"><span data-stu-id="a0d49-128">Other</span></span>  
 <span data-ttu-id="a0d49-129">Outros literais com suporte do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são Guid, Binary, Float/Double, Decimal e `null`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="a0d49-130">Literais nulos em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são considerados compatíveis com cada outro tipo no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="a0d49-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="a0d49-131">Construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="a0d49-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="a0d49-132">ROW</span><span class="sxs-lookup"><span data-stu-id="a0d49-132">ROW</span></span>  
 <span data-ttu-id="a0d49-133">[LINHA](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constrói um valor (registro) anônimo, tipado estruturalmente como em: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="a0d49-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="a0d49-134">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="a0d49-135">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-135">Output:</span></span>  
  
|<span data-ttu-id="a0d49-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="a0d49-136">ProductID</span></span>|<span data-ttu-id="a0d49-137">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d49-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="a0d49-138">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-138">1</span></span>|<span data-ttu-id="a0d49-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="a0d49-139">Adjustable Race</span></span>|  
|<span data-ttu-id="a0d49-140">879</span><span class="sxs-lookup"><span data-stu-id="a0d49-140">879</span></span>|<span data-ttu-id="a0d49-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a0d49-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a0d49-142">712</span><span class="sxs-lookup"><span data-stu-id="a0d49-142">712</span></span>|<span data-ttu-id="a0d49-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="a0d49-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a0d49-144">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-144">...</span></span>|<span data-ttu-id="a0d49-145">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="a0d49-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="a0d49-146">MULTISET</span></span>  
 <span data-ttu-id="a0d49-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constrói coleções, tais como:</span><span class="sxs-lookup"><span data-stu-id="a0d49-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="a0d49-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="a0d49-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="a0d49-149">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="a0d49-150">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-150">Output:</span></span>  
  
|<span data-ttu-id="a0d49-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="a0d49-151">ProductID</span></span>|<span data-ttu-id="a0d49-152">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d49-152">Name</span></span>|<span data-ttu-id="a0d49-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="a0d49-153">ProductNumber</span></span>|<span data-ttu-id="a0d49-154">…</span><span class="sxs-lookup"><span data-stu-id="a0d49-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="a0d49-155">842</span><span class="sxs-lookup"><span data-stu-id="a0d49-155">842</span></span>|<span data-ttu-id="a0d49-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="a0d49-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="a0d49-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="a0d49-157">PA-T100</span></span>|<span data-ttu-id="a0d49-158">…</span><span class="sxs-lookup"><span data-stu-id="a0d49-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="a0d49-159">Objeto</span><span class="sxs-lookup"><span data-stu-id="a0d49-159">Object</span></span>  
 <span data-ttu-id="a0d49-160">[Chamada de construtor do tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constrói objetos definidos pelo usuário (nomeados), como `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="a0d49-161">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="a0d49-162">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-162">Output:</span></span>  
  
|<span data-ttu-id="a0d49-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="a0d49-163">SalesOrderDetailID</span></span>|<span data-ttu-id="a0d49-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="a0d49-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="a0d49-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="a0d49-165">OrderQty</span></span>|<span data-ttu-id="a0d49-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="a0d49-166">ProductID</span></span>|<span data-ttu-id="a0d49-167">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="a0d49-168">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-168">1</span></span>|<span data-ttu-id="a0d49-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="a0d49-169">4911-403C-98</span></span>|<span data-ttu-id="a0d49-170">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-170">1</span></span>|<span data-ttu-id="a0d49-171">776</span><span class="sxs-lookup"><span data-stu-id="a0d49-171">776</span></span>|<span data-ttu-id="a0d49-172">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-172">...</span></span>|  
|<span data-ttu-id="a0d49-173">2</span><span class="sxs-lookup"><span data-stu-id="a0d49-173">2</span></span>|<span data-ttu-id="a0d49-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="a0d49-174">4911-403C-98</span></span>|<span data-ttu-id="a0d49-175">3</span><span class="sxs-lookup"><span data-stu-id="a0d49-175">3</span></span>|<span data-ttu-id="a0d49-176">777</span><span class="sxs-lookup"><span data-stu-id="a0d49-176">777</span></span>|<span data-ttu-id="a0d49-177">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-177">...</span></span>|  
|<span data-ttu-id="a0d49-178">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-178">...</span></span>|<span data-ttu-id="a0d49-179">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-179">...</span></span>|<span data-ttu-id="a0d49-180">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-180">...</span></span>|<span data-ttu-id="a0d49-181">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-181">...</span></span>|<span data-ttu-id="a0d49-182">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="a0d49-183">Referências</span><span class="sxs-lookup"><span data-stu-id="a0d49-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a0d49-184">REF</span><span class="sxs-lookup"><span data-stu-id="a0d49-184">REF</span></span>  
 <span data-ttu-id="a0d49-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) cria uma referência a uma instância do tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="a0d49-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="a0d49-186">Por exemplo, a seguinte consulta retorna referências para cada entidade Order no conjunto de entidades Orders:</span><span class="sxs-lookup"><span data-stu-id="a0d49-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="a0d49-187">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-187">Output:</span></span>  
  
|<span data-ttu-id="a0d49-188">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-189">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-189">1</span></span>|  
|<span data-ttu-id="a0d49-190">2</span><span class="sxs-lookup"><span data-stu-id="a0d49-190">2</span></span>|  
|<span data-ttu-id="a0d49-191">3</span><span class="sxs-lookup"><span data-stu-id="a0d49-191">3</span></span>|  
|<span data-ttu-id="a0d49-192">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-192">...</span></span>|  
  
 <span data-ttu-id="a0d49-193">O exemplo a seguir usa o operador de extração de propriedade (.) para acessar uma propriedade de uma entidade.</span><span class="sxs-lookup"><span data-stu-id="a0d49-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="a0d49-194">Quando o operador de extração de propriedade é usado, a referência é cancelada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a0d49-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="a0d49-195">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="a0d49-196">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-196">Output:</span></span>  
  
|<span data-ttu-id="a0d49-197">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="a0d49-198">Adjustable Race</span></span>|  
|<span data-ttu-id="a0d49-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a0d49-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a0d49-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="a0d49-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a0d49-201">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="a0d49-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="a0d49-202">DEREF</span></span>  
 <span data-ttu-id="a0d49-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) desreferencia um valor de referência e gera o resultado dessa desreferência.</span><span class="sxs-lookup"><span data-stu-id="a0d49-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="a0d49-204">Por exemplo, a seguinte consulta gera as entidades Order para cada Order no conjunto de entidades Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="a0d49-205">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="a0d49-206">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-206">Output:</span></span>  
  
|<span data-ttu-id="a0d49-207">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="a0d49-208">Adjustable Race</span></span>|  
|<span data-ttu-id="a0d49-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a0d49-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a0d49-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="a0d49-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a0d49-211">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="a0d49-212">CREATEREF AND KEY</span><span class="sxs-lookup"><span data-stu-id="a0d49-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="a0d49-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) cria uma referência passando uma chave.</span><span class="sxs-lookup"><span data-stu-id="a0d49-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="a0d49-214">[CHAVE](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrai a parte da chave de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="a0d49-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="a0d49-215">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="a0d49-216">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-216">Output:</span></span>  
  
|<span data-ttu-id="a0d49-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="a0d49-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="a0d49-218">980</span><span class="sxs-lookup"><span data-stu-id="a0d49-218">980</span></span>|  
|<span data-ttu-id="a0d49-219">365</span><span class="sxs-lookup"><span data-stu-id="a0d49-219">365</span></span>|  
|<span data-ttu-id="a0d49-220">771</span><span class="sxs-lookup"><span data-stu-id="a0d49-220">771</span></span>|  
|<span data-ttu-id="a0d49-221">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="a0d49-222">Funções</span><span class="sxs-lookup"><span data-stu-id="a0d49-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="a0d49-223">Canônica</span><span class="sxs-lookup"><span data-stu-id="a0d49-223">Canonical</span></span>  
 <span data-ttu-id="a0d49-224">O namespace [funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) é o Edm, como em `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="a0d49-225">Você não precisa especificar o namespace, a menos que outro namespace seja importado e contenha uma função com o mesmo nome de uma função canônica.</span><span class="sxs-lookup"><span data-stu-id="a0d49-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="a0d49-226">Se dois namespaces têm a mesma função, o usuário deve especificar o nome completo.</span><span class="sxs-lookup"><span data-stu-id="a0d49-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="a0d49-227">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="a0d49-228">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-228">Output:</span></span>  
  
|<span data-ttu-id="a0d49-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="a0d49-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="a0d49-230">6</span><span class="sxs-lookup"><span data-stu-id="a0d49-230">6</span></span>|  
|<span data-ttu-id="a0d49-231">6</span><span class="sxs-lookup"><span data-stu-id="a0d49-231">6</span></span>|  
|<span data-ttu-id="a0d49-232">5</span><span class="sxs-lookup"><span data-stu-id="a0d49-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="a0d49-233">Específico do provedor da Microsoft</span><span class="sxs-lookup"><span data-stu-id="a0d49-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="a0d49-234">[Funções específicas do provedor da Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) estão no `SqlServer` namespace.</span><span class="sxs-lookup"><span data-stu-id="a0d49-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="a0d49-235">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="a0d49-236">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-236">Output:</span></span>  
  
|<span data-ttu-id="a0d49-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="a0d49-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="a0d49-238">27</span><span class="sxs-lookup"><span data-stu-id="a0d49-238">27</span></span>|  
|<span data-ttu-id="a0d49-239">27</span><span class="sxs-lookup"><span data-stu-id="a0d49-239">27</span></span>|  
|<span data-ttu-id="a0d49-240">26</span><span class="sxs-lookup"><span data-stu-id="a0d49-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="a0d49-241">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a0d49-241">Namespaces</span></span>  
 <span data-ttu-id="a0d49-242">[USANDO](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Especifica namespaces usados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a0d49-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="a0d49-243">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="a0d49-244">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-244">Output:</span></span>  
  
|<span data-ttu-id="a0d49-245">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-246">aa</span><span class="sxs-lookup"><span data-stu-id="a0d49-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="a0d49-247">Paginação</span><span class="sxs-lookup"><span data-stu-id="a0d49-247">Paging</span></span>  
 <span data-ttu-id="a0d49-248">Paginação pode ser expressa declarando uma [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas para o [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="a0d49-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="a0d49-249">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="a0d49-250">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-250">Output:</span></span>  
  
|<span data-ttu-id="a0d49-251">ID</span><span class="sxs-lookup"><span data-stu-id="a0d49-251">ID</span></span>|<span data-ttu-id="a0d49-252">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d49-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="a0d49-253">10</span><span class="sxs-lookup"><span data-stu-id="a0d49-253">10</span></span>|<span data-ttu-id="a0d49-254">Adina</span><span class="sxs-lookup"><span data-stu-id="a0d49-254">Adina</span></span>|  
|<span data-ttu-id="a0d49-255">11</span><span class="sxs-lookup"><span data-stu-id="a0d49-255">11</span></span>|<span data-ttu-id="a0d49-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="a0d49-256">Agcaoili</span></span>|  
|<span data-ttu-id="a0d49-257">12</span><span class="sxs-lookup"><span data-stu-id="a0d49-257">12</span></span>|<span data-ttu-id="a0d49-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="a0d49-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="a0d49-259">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="a0d49-259">Grouping</span></span>  
 <span data-ttu-id="a0d49-260">[Agrupar por](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Especifica os grupos nos quais os objetos retornados por uma consulta ([selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expressão devem ser colocados.</span><span class="sxs-lookup"><span data-stu-id="a0d49-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="a0d49-261">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="a0d49-262">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-262">Output:</span></span>  
  
|<span data-ttu-id="a0d49-263">name</span><span class="sxs-lookup"><span data-stu-id="a0d49-263">name</span></span>|  
|----------|  
|<span data-ttu-id="a0d49-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="a0d49-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a0d49-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="a0d49-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a0d49-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="a0d49-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a0d49-267">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="a0d49-268">Navegação</span><span class="sxs-lookup"><span data-stu-id="a0d49-268">Navigation</span></span>  
 <span data-ttu-id="a0d49-269">O operador de navegação de relação permite que você navegue na relação de uma entidade (from end) para outra (to end).</span><span class="sxs-lookup"><span data-stu-id="a0d49-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="a0d49-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) usa o tipo de relação qualificado como \<namespace >.\< nome do tipo de relação >.</span><span class="sxs-lookup"><span data-stu-id="a0d49-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="a0d49-271">Navegue retorna Ref\<T > se a cardinalidade de to end é 1.</span><span class="sxs-lookup"><span data-stu-id="a0d49-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="a0d49-272">Se a cardinalidade de to end for n, a coleção < Ref\<T >> será retornado.</span><span class="sxs-lookup"><span data-stu-id="a0d49-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="a0d49-273">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="a0d49-274">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-274">Output:</span></span>  
  
|<span data-ttu-id="a0d49-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="a0d49-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="a0d49-276">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-276">1</span></span>|  
|<span data-ttu-id="a0d49-277">2</span><span class="sxs-lookup"><span data-stu-id="a0d49-277">2</span></span>|  
|<span data-ttu-id="a0d49-278">3</span><span class="sxs-lookup"><span data-stu-id="a0d49-278">3</span></span>|  
|<span data-ttu-id="a0d49-279">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="a0d49-280">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="a0d49-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="a0d49-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="a0d49-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a0d49-282">fornece a cláusula SELECT VALUE para ignorar a construção de linha implícita.</span><span class="sxs-lookup"><span data-stu-id="a0d49-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="a0d49-283">Somente um item pode ser especificado em uma cláusula SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="a0d49-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="a0d49-284">Quando tal cláusula é usada, nenhum wrapper de linha é construído ao redor dos itens na cláusula SELECT e pode de uma coleção da forma desejada ser gerada, por exemplo: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="a0d49-285">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="a0d49-286">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-286">Output:</span></span>  
  
|<span data-ttu-id="a0d49-287">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d49-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="a0d49-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="a0d49-288">Adjustable Race</span></span>|  
|<span data-ttu-id="a0d49-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a0d49-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a0d49-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="a0d49-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a0d49-291">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="a0d49-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="a0d49-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a0d49-293">também fornece o construtor de linha para construir linhas arbitrárias.</span><span class="sxs-lookup"><span data-stu-id="a0d49-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="a0d49-294">SELECT utiliza um ou mais elementos na projeção e resulta em um registro de dados com campos; por exemplo: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="a0d49-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="a0d49-295">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-295">Example:</span></span>  
  
 <span data-ttu-id="a0d49-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="a0d49-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="a0d49-297">Nome</span><span class="sxs-lookup"><span data-stu-id="a0d49-297">Name</span></span>|<span data-ttu-id="a0d49-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="a0d49-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="a0d49-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="a0d49-299">Adjustable Race</span></span>|<span data-ttu-id="a0d49-300">1</span><span class="sxs-lookup"><span data-stu-id="a0d49-300">1</span></span>|  
|<span data-ttu-id="a0d49-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="a0d49-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="a0d49-302">879</span><span class="sxs-lookup"><span data-stu-id="a0d49-302">879</span></span>|  
|<span data-ttu-id="a0d49-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="a0d49-303">AWC Logo Cap</span></span>|<span data-ttu-id="a0d49-304">712</span><span class="sxs-lookup"><span data-stu-id="a0d49-304">712</span></span>|  
|<span data-ttu-id="a0d49-305">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-305">...</span></span>|<span data-ttu-id="a0d49-306">...</span><span class="sxs-lookup"><span data-stu-id="a0d49-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="a0d49-307">CASE EXPRESSION</span><span class="sxs-lookup"><span data-stu-id="a0d49-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="a0d49-308">O [caso a expressão](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) avalia um conjunto de expressões Boolianas para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="a0d49-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="a0d49-309">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0d49-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="a0d49-310">Saída:</span><span class="sxs-lookup"><span data-stu-id="a0d49-310">Output:</span></span>  
  
|<span data-ttu-id="a0d49-311">Valor</span><span class="sxs-lookup"><span data-stu-id="a0d49-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a0d49-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="a0d49-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0d49-313">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0d49-313">See also</span></span>

- [<span data-ttu-id="a0d49-314">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a0d49-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a0d49-315">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a0d49-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
