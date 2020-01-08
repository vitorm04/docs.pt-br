---
title: 'Como: definir cabeçalhos na solicitação do cliente (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: af158fa525f1f83c081ab293bfdbfb4177caf5a6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348387"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Como: definir cabeçalhos na solicitação do cliente (WCF Data Services)
Quando você usa a biblioteca de cliente WCF Data Services para acessar um serviço de dados que dá suporte ao Protocolo Open Data (OData), a biblioteca de cliente define automaticamente os cabeçalhos HTTP necessários em mensagens de solicitação enviadas para o serviço de dados. No entanto, a biblioteca de cliente não sabe definir cabeçalhos de mensagens que são necessários em determinados casos, como quando o serviço de dados requer autenticação baseada em declarações ou cookies. Para obter mais informações, consulte [securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication). Nesses casos, você deve definir manualmente os cabeçalhos de mensagem na mensagem de solicitação antes que eles sejam enviados. O exemplo neste tópico mostra como manipular o evento <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> para adicionar um novo cabeçalho à mensagem de solicitação antes que ele seja enviado para o serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](https://services.odata.org/Northwind/Northwind.svc/) que é publicado no site do OData; Este serviço de dados de exemplo é somente leitura e a tentativa de salvar alterações retorna um erro. Os serviços de dados de exemplo no site do OData permitem a autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra um manipulador para o evento <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> e, em seguida, executa uma consulta no serviço de dados.  
  
> [!NOTE]
> Quando um serviço de dados exige que você defina manualmente o cabeçalho da mensagem para cada solicitação, considere registrar o manipulador para o evento de <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> substituindo o `OnContextCreated` método parcial no contêiner de entidade que representa o serviço de dados, que nesse caso é `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemplo  
 O método a seguir manipula o evento <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> e adiciona um cabeçalho de autenticação à solicitação.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Veja também

- [Protegendo o WCF Data Services](securing-wcf-data-services.md)
- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
