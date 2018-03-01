---
title: "Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343fc6043b4cfc7ea02ff33c18aaaf5ced14c11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="63941-102">Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="63941-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="63941-103">permite definir um modelo de dados que é baseado em classes arbitrários, desde que essas classes são expostas como objetos que implementam o <xref:System.Linq.IQueryable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="63941-103"> enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="63941-104">Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="63941-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63941-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63941-105">Example</span></span>  
 <span data-ttu-id="63941-106">O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`.</span><span class="sxs-lookup"><span data-stu-id="63941-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="63941-107">A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces.</span><span class="sxs-lookup"><span data-stu-id="63941-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="63941-108">Essas interfaces são os conjuntos de entidade do `Orders` e `Items` tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="63941-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="63941-109">Um `Order` pode incluir vários `Items`, portanto, o `Orders` tipo de entidade tem um `Items` propriedade de navegação que retorna uma coleção de `Items` objetos.</span><span class="sxs-lookup"><span data-stu-id="63941-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="63941-110">O `OrderItemData` classe de contêiner de entidade é o tipo genérico do <xref:System.Data.Services.DataService%601> classe da qual o `OrderItems` serviço de dados é derivado.</span><span class="sxs-lookup"><span data-stu-id="63941-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63941-111">Como este exemplo demonstra um provedor de dados na memória e alterações não são mantidas fora as instâncias do objeto atual, não há nenhuma vantagem derivada de implementar o <xref:System.Data.Services.IUpdatable> interface.</span><span class="sxs-lookup"><span data-stu-id="63941-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="63941-112">Para obter um exemplo que implementa o <xref:System.Data.Services.IUpdatable> interface, consulte [como: criar um serviço de dados usando uma fonte de dados SQL do LINQ](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="63941-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="63941-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63941-113">See Also</span></span>  
 [<span data-ttu-id="63941-114">Como criar um serviço de dados usando uma fonte de dados LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="63941-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [<span data-ttu-id="63941-115">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="63941-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="63941-116">Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="63941-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
