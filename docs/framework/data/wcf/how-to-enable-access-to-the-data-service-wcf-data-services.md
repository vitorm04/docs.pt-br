---
title: 'Como: Habilitar o acesso ao serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 82b2ec9313c6e0d4b9fa05862209a3ea838f31fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918616"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Como: Habilitar o acesso ao serviço de dados (WCF Data Services)
No [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você deve conceder explicitamente acesso aos recursos que são expostos por um serviço de dados. Isso significa que, depois de criar um novo serviço de dados, você ainda deve fornecer acesso explicitamente a recursos individuais como conjuntos de entidades. Este tópico mostra como habilitar o acesso de leitura e gravação para cinco dos conjuntos de entidades no serviço de dados Northwind que é criado quando você conclui o guia de [início rápido](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Como a <xref:System.Data.Services.EntitySetRights> enumeração é definida usando o <xref:System.FlagsAttribute>, você pode usar um operador OR lógico para especificar várias permissões para um único conjunto de entidades.  
  
> [!NOTE]
> Qualquer cliente que possa acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados. Em um serviço de dados de produção, para impedir o acesso não autorizado aos recursos, você também deve proteger o próprio aplicativo. Para obter mais informações, consulte [securing ASP.NET Web sites](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Para habilitar o acesso ao serviço de dados  
  
- No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Isso permite que os clientes tenham acesso de leitura e gravação `Orders` aos `Order_Details` conjuntos de entidades e e acesso somente leitura aos `Customers` conjuntos de entidades.  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenvolver um serviço de dados WCF em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
