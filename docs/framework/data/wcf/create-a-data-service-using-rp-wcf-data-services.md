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
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Como: Criar um serviço de dados usando o provedor de reflexão (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite que você defina um modelo de dados baseado em classes arbitrárias, desde que essas classes sejam expostas como objetos que <xref:System.Linq.IQueryable%601> implementam a interface. Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um modelo de dados `Orders` que `Items`inclui e. A classe `OrderItemData` de contêiner de entidade tem dois métodos públicos <xref:System.Linq.IQueryable%601> que retornam interfaces. Essas interfaces são os conjuntos de entidades dos `Orders` tipos `Items` de entidade e. Um `Order` pode incluir vários `Items`, portanto, `Orders` o tipo de entidade `Items` tem uma propriedade de navegação que retorna `Items` uma coleção de objetos. A `OrderItemData` classe de contêiner de entidade é o tipo genérico <xref:System.Data.Services.DataService%601> da classe da qual `OrderItems` o serviço de dados é derivado.  
  
> [!NOTE]
> Como este exemplo demonstra um provedor de dados na memória e as alterações não são mantidas fora das instâncias do objeto atual, não há nenhum benefício derivado da implementação <xref:System.Data.Services.IUpdatable> da interface. Para obter um exemplo que implementa <xref:System.Data.Services.IUpdatable> a interface, [consulte Como: Crie um serviço de dados usando uma LINQ to SQL fonte](create-a-data-service-using-linq-to-sql-wcf.md)de dados.  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um serviço de dados usando uma fonte de dados LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
- [Provedores de Serviços de Dados](data-services-providers-wcf-data-services.md)
- [Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
