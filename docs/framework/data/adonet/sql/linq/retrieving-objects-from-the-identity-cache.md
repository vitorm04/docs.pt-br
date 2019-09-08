---
title: Recuperando objetos de cache de identidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: d14b15f72bd196d8b3a61f22c614516e17d2e95b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781233"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="1e31b-102">Recuperando objetos de cache de identidade</span><span class="sxs-lookup"><span data-stu-id="1e31b-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="1e31b-103">Este tópico descreve os tipos LINQ to SQL consulta que retornam um objeto de cache de identidade que é gerenciado por <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="1e31b-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="1e31b-104">Em LINQ to SQL, uma das maneiras em que <xref:System.Data.Linq.DataContext> gerencia objetos é autorizando identidades de objeto em um cache de identidade como consultas é executado.</span><span class="sxs-lookup"><span data-stu-id="1e31b-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="1e31b-105">Em alguns casos, LINQ to SQL tentará recuperar um objeto de cache de identidade antes de executar uma consulta na base de dados.</span><span class="sxs-lookup"><span data-stu-id="1e31b-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="1e31b-106">Em geral, porque uma consulta LINQ to SQL para retornar um objeto de cache de identidade, a consulta deve ser baseado a chave primária de um objeto e deve retornar um único objeto.</span><span class="sxs-lookup"><span data-stu-id="1e31b-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="1e31b-107">Em particular, a consulta deve estar em um dos formulários gerais mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="1e31b-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e31b-108">Consultas pré-compilação compiladas não irão retornar objetos de cache de identidade.</span><span class="sxs-lookup"><span data-stu-id="1e31b-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="1e31b-109">Para obter mais informações sobre consultas previamente compiladas, <xref:System.Data.Linq.CompiledQuery> consulte [e como: Armazene e reutilize consultas](how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1e31b-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="1e31b-110">Uma consulta deve estar em um das seguintes formas gerais para recuperar um objeto de cache de identidade:</span><span class="sxs-lookup"><span data-stu-id="1e31b-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="1e31b-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="1e31b-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="1e31b-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="1e31b-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="1e31b-113">Nesses formulários gerais, `Function1`, `Function2`, e `predicate` são definidos como segue.</span><span class="sxs-lookup"><span data-stu-id="1e31b-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="1e31b-114">`Function1` pode ser um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="1e31b-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="1e31b-115">`Function2` pode ser um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="1e31b-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="1e31b-116">`predicate` deve ser uma expressão na propriedade de chave primária de objeto é definida como um valor constante.</span><span class="sxs-lookup"><span data-stu-id="1e31b-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="1e31b-117">Se um objeto tem uma chave primária definida por mais de uma propriedade, cada propriedade de chave primária deve ser definida como um valor constante.</span><span class="sxs-lookup"><span data-stu-id="1e31b-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="1e31b-118">Os seguintes são exemplos de formulário `predicate` devem tomar:</span><span class="sxs-lookup"><span data-stu-id="1e31b-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="1e31b-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e31b-119">Example</span></span>  
 <span data-ttu-id="1e31b-120">O código a seguir fornece exemplos dos tipos de consultas LINQ to SQL que recuperam um objeto de cache de identidade.</span><span class="sxs-lookup"><span data-stu-id="1e31b-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1e31b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e31b-121">See also</span></span>

- [<span data-ttu-id="1e31b-122">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="1e31b-122">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="1e31b-123">Identidade do objeto</span><span class="sxs-lookup"><span data-stu-id="1e31b-123">Object Identity</span></span>](object-identity.md)
- [<span data-ttu-id="1e31b-124">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="1e31b-124">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="1e31b-125">Identidade do objeto</span><span class="sxs-lookup"><span data-stu-id="1e31b-125">Object Identity</span></span>](object-identity.md)
