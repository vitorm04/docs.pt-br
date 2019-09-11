---
title: 'Exemplos de sintaxe de expressão de consulta: Relações de navegação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: a99d7d31ce23629bf7a0f390244c1fe67b4554e3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854414"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="c809d-102">Exemplos de sintaxe de expressão de consulta: Relações de navegação</span><span class="sxs-lookup"><span data-stu-id="c809d-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="c809d-103">As propriedades de navegação no Entity Framework são propriedades de atalho usadas para localizar as entidades nas extremidades de uma associação.</span><span class="sxs-lookup"><span data-stu-id="c809d-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="c809d-104">As propriedades de navegação permitem que um usuário navegue de uma entidade para outra, ou uma entidade a entidades relacionadas por um conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="c809d-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="c809d-105">Este tópico fornece exemplos de sintaxe de expressão de consulta de como navegar em relações por meio de propriedades de navegação em LINQ to Entities consultas.</span><span class="sxs-lookup"><span data-stu-id="c809d-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="c809d-106">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c809d-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c809d-107">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="c809d-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="c809d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c809d-108">Example</span></span>  
 <span data-ttu-id="c809d-109">O exemplo a seguir usa o método de <xref:System.Linq.Queryable.Select%2A> para obter todos os IDs de contato e soma total de vencido para cada contato cujo nome é “Zhou”.</span><span class="sxs-lookup"><span data-stu-id="c809d-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="c809d-110">A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato.</span><span class="sxs-lookup"><span data-stu-id="c809d-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="c809d-111">O método de `Sum` usa a propriedade de navegação de `Contact.SalesOrderHeader` para somar o total vencido de todos os pedidos para cada contato.</span><span class="sxs-lookup"><span data-stu-id="c809d-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="c809d-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c809d-112">Example</span></span>  
 <span data-ttu-id="c809d-113">O exemplo a seguir obtém todos os pedidos de contatos cujo nome é “Zhou”.</span><span class="sxs-lookup"><span data-stu-id="c809d-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="c809d-114">A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato.</span><span class="sxs-lookup"><span data-stu-id="c809d-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="c809d-115">O nome e os pedidos de contato são retornados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="c809d-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="c809d-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c809d-116">Example</span></span>  
 <span data-ttu-id="c809d-117">O exemplo a seguir usa `SalesOrderHeader.Address` e propriedades de navegação de `SalesOrderHeader.Contact` obtém a coleção de `Address` e `Contact` objetos associado com cada pedido.</span><span class="sxs-lookup"><span data-stu-id="c809d-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="c809d-118">O primeiro contato, endereço, o número de ordem de venda, e o total vencido para cada pedido a cidade de Seattle são retornados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="c809d-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="c809d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c809d-119">Example</span></span>  
 <span data-ttu-id="c809d-120">O exemplo a seguir usa o método `Where` para localizar os pedidos que foram feitos depois de 1° de dezembro de 2003 e, em seguida, usa a propriedade de navegação `order.SalesOrderDetail` para obter os detalhes de cada pedido.</span><span class="sxs-lookup"><span data-stu-id="c809d-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="c809d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c809d-121">See also</span></span>

- [<span data-ttu-id="c809d-122">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c809d-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
