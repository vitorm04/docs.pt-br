---
title: 'Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791002"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="c9d30-102">Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c9d30-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="c9d30-103">permite que você defina um modelo de dados baseado em classes arbitrárias, desde que essas classes sejam expostas como objetos que <xref:System.Linq.IQueryable%601> implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="c9d30-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="c9d30-104">Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c9d30-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9d30-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9d30-105">Example</span></span>  
 <span data-ttu-id="c9d30-106">O exemplo a seguir define um modelo de dados `Orders` que `Items`inclui e.</span><span class="sxs-lookup"><span data-stu-id="c9d30-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="c9d30-107">A classe `OrderItemData` de contêiner de entidade tem dois métodos públicos <xref:System.Linq.IQueryable%601> que retornam interfaces.</span><span class="sxs-lookup"><span data-stu-id="c9d30-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="c9d30-108">Essas interfaces são os conjuntos de entidades dos `Orders` tipos `Items` de entidade e.</span><span class="sxs-lookup"><span data-stu-id="c9d30-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="c9d30-109">Um `Order` pode incluir vários `Items`, portanto, `Orders` o tipo de entidade `Items` tem uma propriedade de navegação que retorna `Items` uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="c9d30-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="c9d30-110">A `OrderItemData` classe de contêiner de entidade é o tipo genérico <xref:System.Data.Services.DataService%601> da classe da qual `OrderItems` o serviço de dados é derivado.</span><span class="sxs-lookup"><span data-stu-id="c9d30-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9d30-111">Como este exemplo demonstra um provedor de dados na memória e as alterações não são mantidas fora das instâncias do objeto atual, não há nenhum benefício derivado da implementação <xref:System.Data.Services.IUpdatable> da interface.</span><span class="sxs-lookup"><span data-stu-id="c9d30-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="c9d30-112">Para obter um exemplo que implementa <xref:System.Data.Services.IUpdatable> a interface, [consulte Como: Crie um serviço de dados usando uma LINQ to SQL fonte](create-a-data-service-using-linq-to-sql-wcf.md)de dados.</span><span class="sxs-lookup"><span data-stu-id="c9d30-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="c9d30-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d30-113">See also</span></span>

- [<span data-ttu-id="c9d30-114">Como: Criar um serviço de dados usando uma fonte de dados LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c9d30-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="c9d30-115">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="c9d30-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="c9d30-116">Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9d30-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
