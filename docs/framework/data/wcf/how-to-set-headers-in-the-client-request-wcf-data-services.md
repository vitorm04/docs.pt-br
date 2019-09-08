---
title: 'Como: Definir cabeçalhos na solicitação do cliente (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 42987b1a855589954d45dae13b70ffc056c35f3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790472"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Como: Definir cabeçalhos na solicitação do cliente (WCF Data Services)
Quando você usa a [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente para acessar um serviço de dados que [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]dá suporte ao, a biblioteca de cliente define automaticamente os cabeçalhos HTTP necessários nas mensagens de solicitação enviadas ao serviço de dados. No entanto, a biblioteca de cliente não sabe definir cabeçalhos de mensagens que são necessários em determinados casos, como quando o serviço de dados requer autenticação baseada em declarações ou cookies. Para obter mais informações, consulte [securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication). Nesses casos, você deve definir manualmente os cabeçalhos de mensagem na mensagem de solicitação antes que eles sejam enviados. O exemplo neste tópico mostra como manipular o <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> evento para adicionar um novo cabeçalho à mensagem de solicitação antes que ele seja enviado ao serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) publicado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site; esse serviço de dados de exemplo é somente leitura e a tentativa de salvar alterações retorna um erro. Os serviços de dados de exemplo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] no site permitem autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra um manipulador para <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> o evento e, em seguida, executa uma consulta no serviço de dados.  
  
> [!NOTE]
> Quando um serviço de dados exige que você defina manualmente o cabeçalho da mensagem para cada solicitação, considere registrar o manipulador para <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> o evento, substituindo o `OnContextCreated` método parcial no contêiner de entidade que representa o serviço de dados, que no Esse caso é `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Exemplo  
 O método a seguir trata <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> o evento e adiciona um cabeçalho de autenticação à solicitação.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Consulte também

- [Protegendo o WCF Data Services](securing-wcf-data-services.md)
- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
