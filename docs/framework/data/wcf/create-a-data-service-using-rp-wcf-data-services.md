---
title: "Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11f01a88e1d276321384f00f3e103322ccaef339
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>Como: criar um serviço de dados usando o provedor de reflexão (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite definir um modelo de dados que é baseado em classes arbitrários, desde que essas classes são expostas como objetos que implementam o <xref:System.Linq.IQueryable%601> interface. Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um modelo de dados que inclui `Orders` e `Items`. A classe de contêiner de entidade `OrderItemData` tem dois métodos públicos que retornam <xref:System.Linq.IQueryable%601> interfaces. Essas interfaces são os conjuntos de entidade do `Orders` e `Items` tipos de entidade. Um `Order` pode incluir vários `Items`, portanto, o `Orders` tipo de entidade tem um `Items` propriedade de navegação que retorna uma coleção de `Items` objetos. O `OrderItemData` classe de contêiner de entidade é o tipo genérico do <xref:System.Data.Services.DataService%601> classe da qual o `OrderItems` serviço de dados é derivado.  
  
> [!NOTE]
>  Como este exemplo demonstra um provedor de dados na memória e alterações não são mantidas fora as instâncias do objeto atual, não há nenhuma vantagem derivada de implementar o <xref:System.Data.Services.IUpdatable> interface. Para obter um exemplo que implementa o <xref:System.Data.Services.IUpdatable> interface, consulte [como: criar um serviço de dados usando uma fonte de dados SQL do LINQ](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um serviço de dados usando um LINQ para a fonte de dados SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [Provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Como: criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
