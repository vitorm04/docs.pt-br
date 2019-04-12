---
title: 'Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517090"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="5017c-102">Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5017c-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="5017c-103">permite que você defina um modelo de dados é baseado em classes arbitrárias, desde que essas classes são expostas como objetos que implementam o <xref:System.Linq.IQueryable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="5017c-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="5017c-104">Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5017c-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5017c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5017c-105">Example</span></span>  
 <span data-ttu-id="5017c-106">O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`.</span><span class="sxs-lookup"><span data-stu-id="5017c-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="5017c-107">A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces.</span><span class="sxs-lookup"><span data-stu-id="5017c-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="5017c-108">Essas interfaces são os conjuntos de entidades do `Orders` e `Items` tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="5017c-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="5017c-109">Uma `Order` pode incluir vários `Items`, portanto, o `Orders` tipo de entidade tem uma `Items` propriedade de navegação que retorna uma coleção de `Items` objetos.</span><span class="sxs-lookup"><span data-stu-id="5017c-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="5017c-110">O `OrderItemData` classe de contêiner de entidade é o tipo genérico do <xref:System.Data.Services.DataService%601> classe da qual o `OrderItems` serviço de dados é derivado.</span><span class="sxs-lookup"><span data-stu-id="5017c-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5017c-111">Como este exemplo demonstra um provedor de dados na memória e as alterações não são persistidas fora as instâncias de objeto atual, não há nenhum benefício que derivado de implementar o <xref:System.Data.Services.IUpdatable> interface.</span><span class="sxs-lookup"><span data-stu-id="5017c-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="5017c-112">Para obter um exemplo que implementa o <xref:System.Data.Services.IUpdatable> interface, consulte [como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="5017c-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="5017c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5017c-113">See also</span></span>

- [<span data-ttu-id="5017c-114">Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL</span><span class="sxs-lookup"><span data-stu-id="5017c-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="5017c-115">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="5017c-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="5017c-116">Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5017c-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
