---
title: 'Como: Habilitar o acesso ao serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 260d127107d1ccf1263f4efddd59da9e34306436
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645647"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Como: Habilitar o acesso ao serviço de dados (WCF Data Services)
No [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você deve conceder explicitamente acesso aos recursos que são expostos por um serviço de dados. Isso significa que, depois de criar um novo serviço de dados, você deve explicitamente ainda fornecer acesso aos recursos individuais, como conjuntos de entidades. Este tópico mostra como habilitar a leitura e acesso de gravação para cinco da entidade define no serviço de dados Northwind é criado quando você conclui o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Porque o <xref:System.Data.Services.EntitySetRights> enumeração é definida usando o <xref:System.FlagsAttribute>, você pode usar uma lógica ou operador para especificar várias permissões para uma única entidade definida.  
  
> [!NOTE]
>  Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados. Em um serviço de dados de produção, para evitar acesso não autorizado aos recursos, você deve também proteger o próprio aplicativo. Para obter mais informações, consulte [Protegendo Sites da Web de ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Para habilitar o acesso ao serviço de dados  
  
- No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Isso permite que os clientes tenha de leitura e acesso de gravação para o `Orders` e `Order_Details` conjuntos de entidades e acesso somente leitura para o `Customers` conjuntos de entidades.  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
