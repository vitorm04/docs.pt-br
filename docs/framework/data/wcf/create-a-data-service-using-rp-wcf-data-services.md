---
title: 'Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569289"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="55644-102">Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="55644-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="55644-103">WCF Data Services permite que você defina um modelo de dados baseado em classes arbitrárias, desde que essas classes sejam expostas como objetos que implementam a interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="55644-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="55644-104">Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="55644-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55644-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55644-105">Example</span></span>  
 <span data-ttu-id="55644-106">O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`.</span><span class="sxs-lookup"><span data-stu-id="55644-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="55644-107">A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces.</span><span class="sxs-lookup"><span data-stu-id="55644-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="55644-108">Essas interfaces são os conjuntos de entidades dos tipos de entidade `Orders` e `Items`.</span><span class="sxs-lookup"><span data-stu-id="55644-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="55644-109">Um `Order` pode incluir vários `Items`, portanto, o tipo de entidade `Orders` tem uma propriedade de navegação `Items` que retorna uma coleção de objetos `Items`.</span><span class="sxs-lookup"><span data-stu-id="55644-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="55644-110">A classe de contêiner de entidade `OrderItemData` é o tipo genérico da classe <xref:System.Data.Services.DataService%601> da qual o serviço de dados `OrderItems` é derivado.</span><span class="sxs-lookup"><span data-stu-id="55644-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55644-111">Como este exemplo demonstra um provedor de dados na memória e as alterações não são mantidas fora das instâncias do objeto atual, não há nenhum benefício derivado da implementação da interface <xref:System.Data.Services.IUpdatable>.</span><span class="sxs-lookup"><span data-stu-id="55644-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="55644-112">Para obter um exemplo que implementa a interface <xref:System.Data.Services.IUpdatable>, consulte [como criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="55644-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="55644-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55644-113">See also</span></span>

- [<span data-ttu-id="55644-114">Como criar um serviço de dados usando uma fonte de dados LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="55644-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="55644-115">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="55644-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="55644-116">Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="55644-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
