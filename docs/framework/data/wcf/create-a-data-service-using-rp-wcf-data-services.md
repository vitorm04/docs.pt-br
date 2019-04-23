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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517090"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que você defina um modelo de dados é baseado em classes arbitrárias, desde que essas classes são expostas como objetos que implementam o <xref:System.Linq.IQueryable%601> interface. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`. A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces. Essas interfaces são os conjuntos de entidades do `Orders` e `Items` tipos de entidade. Uma `Order` pode incluir vários `Items`, portanto, o `Orders` tipo de entidade tem uma `Items` propriedade de navegação que retorna uma coleção de `Items` objetos. O `OrderItemData` classe de contêiner de entidade é o tipo genérico do <xref:System.Data.Services.DataService%601> classe da qual o `OrderItems` serviço de dados é derivado.  
  
> [!NOTE]
>  Como este exemplo demonstra um provedor de dados na memória e as alterações não são persistidas fora as instâncias de objeto atual, não há nenhum benefício que derivado de implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter um exemplo que implementa o <xref:System.Data.Services.IUpdatable> interface, consulte [como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Provedores de Serviços de Dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
