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
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)
WCF Data Services permite que você defina um modelo de dados baseado em classes arbitrárias, desde que essas classes sejam expostas como objetos que implementam a interface <xref:System.Linq.IQueryable%601>. Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`. A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces. Essas interfaces são os conjuntos de entidades dos tipos de entidade `Orders` e `Items`. Um `Order` pode incluir vários `Items`, portanto, o tipo de entidade `Orders` tem uma propriedade de navegação `Items` que retorna uma coleção de objetos `Items`. A classe de contêiner de entidade `OrderItemData` é o tipo genérico da classe <xref:System.Data.Services.DataService%601> da qual o serviço de dados `OrderItems` é derivado.  
  
> [!NOTE]
> Como este exemplo demonstra um provedor de dados na memória e as alterações não são mantidas fora das instâncias do objeto atual, não há nenhum benefício derivado da implementação da interface <xref:System.Data.Services.IUpdatable>. Para obter um exemplo que implementa a interface <xref:System.Data.Services.IUpdatable>, consulte [como criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Consulte também

- [Como criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
