---
title: 'Como: Definir os cabeçalhos da solicitação do cliente (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: bbf306b31dd2bc9cfcfb877351205970fc63706f
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517883"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Como: Definir os cabeçalhos da solicitação do cliente (WCF Data Services)
Quando você usa o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente para acessar um serviço de dados que oferece suporte a [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], a biblioteca de cliente define automaticamente os cabeçalhos HTTP necessários nas mensagens de solicitação enviadas ao serviço de dados. No entanto, a biblioteca de cliente não sabe para definir os cabeçalhos de mensagem que são necessários em determinados casos, como quando o serviço de dados requer a autenticação baseada em declarações ou cookies. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). Nesses casos, você deve definir manualmente os cabeçalhos de mensagem na mensagem de solicitação antes de serem enviado. O exemplo neste tópico mostra como tratar o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento para adicionar um novo cabeçalho para a mensagem de solicitação antes de serem enviado ao serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) que é publicado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web; esses dados de exemplo serviço é somente leitura e a tentativa de salvar as alterações retornará um erro. Serviços de dados de exemplo no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web permitem que a autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra um manipulador para o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> eventos e, em seguida, executa uma consulta no serviço de dados.  
  
> [!NOTE]
>  Quando um serviço de dados exige que você definir manualmente o cabeçalho da mensagem para cada solicitação, considere registrar o manipulador para o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento, substituindo o `OnContextCreated` método parcial no contêiner de entidade que representa os dados de serviço, que, em Nesse caso é `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemplo  
 O método a seguir trata a <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> eventos e adiciona um cabeçalho de autenticação para a solicitação.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Consulte também

- [Protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
