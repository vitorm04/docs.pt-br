---
title: "Como: habilitar o acesso ao serviço de dados (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f481a3a918282bf598277dcd4e1bf29d63edddc1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Como: habilitar o acesso ao serviço de dados (WCF Data Services)
Em [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você deve conceder explicitamente acesso a recursos que são expostos por um serviço de dados. Isso significa que, depois de criar um novo serviço de dados, você deve ainda explicitamente fornecer acesso a recursos individuais, como conjuntos de entidades. Este tópico mostra como habilitar a leitura e acesso de gravação a cinco da entidade define no serviço de dados Northwind é criado quando você concluir o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Porque o <xref:System.Data.Services.EntitySetRights> enumeração é definida usando o <xref:System.FlagsAttribute>, você pode usar uma lógica ou conjunto de operador para especificar várias permissões para uma única entidade.  
  
> [!NOTE]
>  Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados. Em um serviço de dados de produção, para evitar acesso não autorizado aos recursos, você deve também proteger o aplicativo em si. Para obter mais informações, consulte [NIB: segurança ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Para habilitar o acesso ao serviço de dados  
  
-   No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Isso permite que os clientes leram e acesso de gravação para o `Orders` e `Order_Details` conjuntos de entidade e acesso somente leitura para o `Customers` conjuntos de entidades.  
  
## <a name="see-also"></a>Consulte também  
 [Como desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
