---
title: 'Como: Definir cabeçalhos na solicitação do cliente (Serviços de dados WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174336"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Como: Definir cabeçalhos na solicitação do cliente (Serviços de dados WCF)
Quando você usa a biblioteca de clientes do WCF Data Services para acessar um serviço de dados que suporta o OData (Open Data Protocol), a biblioteca do cliente define automaticamente os cabeçalhos HTTP necessários nas mensagens de solicitação enviadas ao serviço de dados. No entanto, a biblioteca do cliente não sabe definir cabeçalhos de mensagem que são necessários em certos casos, como quando o serviço de dados requer autenticação ou cookies baseados em sinistros. Para obter mais informações, consulte [Protegendo os Serviços de Dados WCF](securing-wcf-data-services.md#clientAuthentication). Nestes casos, você deve definir manualmente cabeçalhos de mensagem na mensagem de solicitação antes de ser enviada. O exemplo neste tópico mostra <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> como lidar com o evento para adicionar um novo cabeçalho à mensagem de solicitação antes de ser enviado ao serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Este serviço e as classes de dados do cliente são criadas quando você completa o [início rápido dos Serviços de Dados wcf](quickstart-wcf-data-services.md). Você também pode usar o serviço de [dados de amostra northwind](https://services.odata.org/Northwind/Northwind.svc/) que é publicado no site da OData; este serviço de dados de amostra é somente leitura e tentar salvar alterações retorna um erro. Os serviços de dados de amostra no site oData permitem autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> um manipulador para o evento e, em seguida, executa uma consulta contra o serviço de dados.  
  
> [!NOTE]
> Quando um serviço de dados exige que você defina manualmente o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> cabeçalho da `OnContextCreated` mensagem para cada solicitação, considere registrar o manipulador `NorthwindEntities`para o evento, substituindo o método parcial no contêiner da entidade que representa o serviço de dados, que neste caso é .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemplo  
 O método a <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> seguir lida com o evento e adiciona um cabeçalho de autenticação à solicitação.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Confira também

- [Protegendo o WCF Data Services](securing-wcf-data-services.md)
- [Biblioteca de cliente do WCF Data Services](wcf-data-services-client-library.md)
