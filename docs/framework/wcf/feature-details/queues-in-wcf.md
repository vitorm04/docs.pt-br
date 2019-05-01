---
title: Filas no Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: e28c91a8cc1798a4d0cd690f72e503b687af0108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046437"
---
# <a name="queues-in-windows-communication-foundation"></a>Filas no Windows Communication Foundation
Os tópicos desta seção discutem o suporte do Windows Communication Foundation (WCF) para filas. O WCF fornece suporte para enfileiramento de mensagens por aproveitando Microsoft Message Queuing (anteriormente conhecido como MSMQ) como um transporte e permite os seguintes cenários:  
  
- Aplicativos flexíveis. Aplicativos de envio podem enviar mensagens a filas sem a necessidade de saber se o aplicativo de recebimento está disponível para processar a mensagem. A fila fornece independência de processamento que permite que um aplicativo de envio enviar mensagens à fila em uma taxa que não depende de quão rápido os aplicativos de recebimento podem processar as mensagens. Em geral disponibilidade do sistema aumenta ao enviar mensagens para uma fila não está acoplada para processamento de mensagens.  
  
- Isolamento de falha. Aplicativos de envio ou recebimento de mensagens para uma fila podem falhar sem afetar a outra. Se, por exemplo, o aplicativo de recebimento falhar, o aplicativo de envio pode continuar a enviar mensagens à fila. Quando o destinatário estiver funcionando novamente, ele pode processar as mensagens da fila. Isolamento de falha aumenta a disponibilidade e confiabilidade geral do sistema.  
  
- Nivelamento de carga. Aplicativos de envio podem sobrecarregar a aplicativos de recebimento com mensagens. As filas podem gerenciar taxas de produção e consumo de mensagens incompatíveis para que um destinatário não seja sobrecarregado.  
  
- Operações desconectadas. Envio, recebimento e operações de processamento podem ser desconectados ao se comunicar por redes de alta latência ou disponibilidade limitada, como no caso de dispositivos móveis. As filas permitem que essas operações continuar, mesmo quando os pontos de extremidade são desconectados. Quando a conexão for restabelecida, a fila encaminha mensagens para o aplicativo de recebimento.  
  
 Para usar o recurso de filas em um aplicativo WCF, você pode usar uma das associações padrão, ou você pode criar uma ligação personalizada, se uma das associações padrão não atender às suas necessidades. Para obter mais informações sobre associações padrão relevantes e como escolher um, consulte [como: Trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Para obter mais informações sobre como criar associações personalizadas, confira [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Uma visão geral dos conceitos de enfileiramento de mensagens.  
  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Uma visão geral do suporte de fila do WCF.  
  
 [Como: Troca de mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Explica como usar o <xref:System.ServiceModel.NetMsmqBinding> classe para a comunicação entre um cliente WCF e o serviço WCF.  
  
 [Como: Trocar mensagens com pontos de extremidade do WCF e aplicativos do serviço de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Explica como usar o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para comunicação entre aplicativos WCF e o enfileiramento de mensagens.  
  
 [Agrupamento de mensagens em fila em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Explica como agrupar mensagens em uma fila para facilitar o processamento de mensagem correlacionada por um único aplicativo de recebimento.  
  
 [Mensagens em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Explica como mensagens em uma transação em lote.  
  
 [Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Explica como lidar com falhas de transferência e a entrega de mensagem usando filas de mensagens mortas e como processar as mensagens da fila de mensagens mortas.  
  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Explica como tratar mensagens suspeitas (mensagens que excederam o número máximo de tentativas de entrega para o aplicativo de recebimento).  
  
 [Diferenças de recursos da Fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Resume as diferenças na funcionalidade entre filas WCF [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Protegendo mensagens usando a segurança do transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Descreve como usar a segurança de transporte para proteger mensagens em fila.  
  
 [Protegendo as mensagens com segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Descreve como usar a segurança de mensagem para proteger mensagens em fila.  
  
 [Solução de problemas de mensagens em fila](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Explica como solucionar problemas comuns de enfileiramento de mensagens.  
  
 [Práticas recomendadas para a comunicação em fila](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Explica as práticas recomendadas para uso do WCF de comunicação em fila.  
