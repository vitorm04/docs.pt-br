---
title: "Como: definir os cabeçalhos da solicitação do cliente (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62bd78c58f83e0fbe2a6d8ed08104b15e183001b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Como: definir os cabeçalhos da solicitação do cliente (WCF Data Services)
Quando você usa o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente para acessar um serviço de dados que oferece suporte a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], a biblioteca de cliente automaticamente define os cabeçalhos HTTP necessários em mensagens de solicitação enviadas para o serviço de dados. No entanto, a biblioteca de cliente não sabe para definir cabeçalhos de mensagens que são necessários em determinados casos, como quando o serviço de dados requer a autenticação baseada em declarações ou cookies. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Nesses casos, você deve definir manualmente os cabeçalhos de mensagem na mensagem de solicitação antes de ser enviada. O exemplo neste tópico mostra como tratar o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento para adicionar um novo cabeçalho para a mensagem de solicitação antes de serem enviado ao serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](http://go.microsoft.com/fwlink/?LinkId=187426) que é publicado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web; esses dados de exemplo serviço é somente leitura e tentar salvar alterações retornará um erro. Serviços de dados de exemplo no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web permite a autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra um manipulador para o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento e, em seguida, executa uma consulta em relação ao serviço de dados.  
  
> [!NOTE]
>  Quando um serviço de dados exige que você definir manualmente o cabeçalho da mensagem para cada solicitação, considere a possibilidade de registrar o manipulador de <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento, substituindo o `OnContextCreated` método parcial no contêiner de entidade que representa os dados de serviço, que, em Nesse caso é `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemplo  
 O método a seguir trata o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> eventos e adiciona um cabeçalho de autenticação para a solicitação.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
