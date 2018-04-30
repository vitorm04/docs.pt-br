---
title: Filas no Windows Communication Foundation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 82eb421b86f57cfe7c9a23de3ab24de2d4c470cb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="queues-in-windows-communication-foundation"></a>Filas no Windows Communication Foundation
Os tópicos desta seção discutem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporte para filas. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte para enfileiramento de mensagens, aproveitando o enfileiramento de mensagens do Microsoft (anteriormente conhecido como MSMQ) como um transporte e permite que os seguintes cenários:  
  
-   Aplicativos acoplados de forma flexível. Aplicativos de envio podem enviar mensagens para filas, sem a necessidade de saber se o aplicativo de recebimento está disponível para processar a mensagem. A fila fornece independência de processamento que permite que um aplicativo de envio enviar mensagens para a fila em uma taxa que não depende da rapidez os aplicativos receptor podem processar as mensagens. Geral a disponibilidade do sistema aumenta quando enviar mensagens para uma fila não está estreitamente acoplado ao processamento de mensagem.  
  
-   Isolamento de falha. Aplicativos enviar ou receber mensagens para uma fila podem falhar sem afetar uns aos outros. Se, por exemplo, o aplicativo de recebimento falhar, o aplicativo de envio pode continuar a enviar mensagens à fila. Quando o receptor for para cima novamente, ele pode processar as mensagens da fila. Isolamento de falha aumenta a confiabilidade gerais do sistema e a disponibilidade.  
  
-   Nivelamento de carga. Aplicativos de envio podem sobrecarregar a aplicativos de recebimento com mensagens. As filas podem gerenciar taxas de produção e o consumo de mensagens incompatível para que um destinatário não está sobrecarregado.  
  
-   Operações desconectadas. Enviar, receber e processar as operações podem ser desconectados ao se comunicar por redes de alta latência ou disponibilidade limitada, como no caso de dispositivos móveis. As filas permitem que essas operações continuar, mesmo quando os pontos de extremidade são desconectados. Quando a conexão for restabelecida, a fila encaminha mensagens para o aplicativo de recebimento.  
  
 Para usar o recurso de filas em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, você pode usar uma das associações padrão, ou você pode criar uma associação personalizada se uma das associações padrão não atender às suas necessidades. Para obter mais informações sobre associações padrão relevantes e como escolher um, consulte [como: troca mensagens com pontos de extremidade do WCF e aplicativos de serviço de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Para obter mais informações sobre como criar associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Uma visão geral dos conceitos de enfileiramento de mensagens.  
  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Uma visão geral de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporte de fila.  
  
 [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Explica como usar o <xref:System.ServiceModel.NetMsmqBinding> classe para a comunicação entre um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Explica como usar o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para comunicação entre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e aplicativos de enfileiramento de mensagens.  
  
 [Agrupamento de mensagens em fila em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Explica como agrupar mensagens em uma fila para facilitar o processamento de mensagem correlacionado a um único aplicativo de recebimento.  
  
 [Mensagens em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Explica como lote de mensagens em uma transação.  
  
 [Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Explica como lidar com falhas de transferência e a entrega de mensagem usando filas de mensagens mortas e como processar mensagens da fila de mensagens mortas.  
  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Explica como manipular mensagens suspeitas (mensagens excederam o número máximo de tentativas de entrega para o aplicativo de recebimento).  
  
 [Diferenças de recursos da Fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Resume as diferenças entre o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] filas de recurso entre [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
 [Protegendo mensagens usando a segurança do transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Descreve como usar a segurança de transporte para proteger mensagens em fila.  
  
 [Protegendo as mensagens com segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Descreve como usar a segurança de mensagem para proteger mensagens em fila.  
  
 [Solução de problemas de mensagens em fila](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Explica como solucionar problemas comuns de enfileiramento de mensagens.  
  
 [Práticas recomendadas para a comunicação em fila](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Explica as práticas recomendadas para usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comunicação em fila.  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento de mensagens](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)
