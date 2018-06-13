---
title: 'Exemplos de sintaxe da consulta com base em método: Navegando em relações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 6435cf097b2fab880271d2c79ac8bb1afaf9cb6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763209"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="09349-102">Exemplos de sintaxe da consulta com base em método: Navegando em relações</span><span class="sxs-lookup"><span data-stu-id="09349-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="09349-103">Propriedades de navegação no [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] são propriedades do atalho usadas para localizar as entidades nas extremidades de uma associação.</span><span class="sxs-lookup"><span data-stu-id="09349-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="09349-104">As propriedades de navegação permitem que um usuário navegue de uma entidade para outra, ou uma entidade a entidades relacionadas por um conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="09349-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="09349-105">Este tópico fornece exemplos na sintaxe da consulta com base em método de como navegar em relações entre as propriedades de navegação em consultas de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="09349-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="09349-106">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="09349-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="09349-107">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="09349-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="09349-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09349-108">Example</span></span>  
 <span data-ttu-id="09349-109">O exemplo a seguir na sintaxe da consulta com base em método usa o método de <xref:System.Linq.Queryable.SelectMany%2A> para obter todos os pedidos de contatos cujo nome é “Zhou”.</span><span class="sxs-lookup"><span data-stu-id="09349-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="09349-110">A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato.</span><span class="sxs-lookup"><span data-stu-id="09349-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="09349-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09349-111">Example</span></span>  
 <span data-ttu-id="09349-112">O exemplo a seguir na sintaxe da consulta com base em método usa o método de <xref:System.Linq.Queryable.Select%2A> para obter todos os IDs de contato e soma total de vencido para cada contato cujo nome é “Zhou”.</span><span class="sxs-lookup"><span data-stu-id="09349-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="09349-113">A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato.</span><span class="sxs-lookup"><span data-stu-id="09349-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="09349-114">O método de `Sum` usa a propriedade de navegação de `Contact.SalesOrderHeader` para somar o total vencido de todos os pedidos para cada contato.</span><span class="sxs-lookup"><span data-stu-id="09349-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="09349-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09349-115">Example</span></span>  
 <span data-ttu-id="09349-116">O exemplo a seguir na sintaxe da consulta com base em método obtém todos os pedidos de contatos cujo nome é “Zhou”.</span><span class="sxs-lookup"><span data-stu-id="09349-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="09349-117">A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato.</span><span class="sxs-lookup"><span data-stu-id="09349-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="09349-118">O nome e os pedidos de contato são retornados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="09349-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="09349-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09349-119">Example</span></span>  
 <span data-ttu-id="09349-120">O exemplo a seguir usa `SalesOrderHeader.Address` e propriedades de navegação de `SalesOrderHeader.Contact` para obter a coleção de `Address` e de `Contact` objeto associado com cada pedido.</span><span class="sxs-lookup"><span data-stu-id="09349-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="09349-121">O primeiro contato, endereço, o número de ordem de venda, e o total vencido para cada pedido a cidade de Seattle são retornados em um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="09349-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="09349-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09349-122">Example</span></span>  
 <span data-ttu-id="09349-123">O exemplo a seguir usa o método `Where` para localizar os pedidos que foram feitos depois de 1° de dezembro de 2003 e, em seguida, usa a propriedade de navegação `order.SalesOrderDetail` para obter os detalhes de cada pedido.</span><span class="sxs-lookup"><span data-stu-id="09349-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="09349-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09349-124">See Also</span></span>  
 [<span data-ttu-id="09349-125">Propriedades de navegação</span><span class="sxs-lookup"><span data-stu-id="09349-125">Navigation Properties</span></span>](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [<span data-ttu-id="09349-126">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="09349-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
