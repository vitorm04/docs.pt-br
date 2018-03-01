---
title: "Diferenças de funcionalidades em fila no Windows Vista, Windows Server 2003, e no Windows XP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f30ad7819a570f0149868502261f986f4dd8c0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Diferenças de funcionalidades em fila no Windows Vista, Windows Server 2003, e no Windows XP
Este tópico resume as diferenças entre o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] filas de recurso entre [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Fila de mensagens mortas específicas do aplicativo  
 Mensagens em fila podem permanecer na fila indefinidamente se o aplicativo de recebimento não lê-los de maneira oportuna. Esse comportamento não é recomendado se as mensagens são sensíveis ao tempo. Mensagens de detecção de hora têm um `TimeToLive` propriedade definida na associação em fila. Essa propriedade indica quanto tempo as mensagens podem ficar na fila antes de expirarem. As mensagens expiradas são enviadas para uma fila especial chamada fila de mensagens mortas. Uma mensagem também pode terminar em uma fila de mensagens mortas por outros motivos, como exceder uma cota de fila ou devido a uma falha de autenticação.  
  
 Normalmente, uma única fila de mensagens mortas de todo o sistema existe para todos os aplicativos em fila que compartilham um Gerenciador de fila. Uma fila de mensagens mortas para cada aplicativo permite melhor isolamento entre aplicativos em fila que compartilham um Gerenciador de fila, permitindo que esses aplicativos especificar sua própria fila de mensagens mortas específicas do aplicativo. Tem um aplicativo que compartilha uma fila de mensagens mortas com outros aplicativos procurar a fila para localizar as mensagens que se aplicam a ele. Com uma fila de mensagens mortas específicas do aplicativo, o aplicativo pode ter certeza de que todas as mensagens na fila de mensagens mortas são aplicáveis a ele.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]fornece para filas de mensagens mortas específicas do aplicativo. Filas de mensagens mortas específicas do aplicativo não estão disponíveis em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], e os aplicativos devem usar a fila de mensagens mortas de todo o sistema.  
  
## <a name="poison-message-handling"></a>Tratamento de mensagens suspeitas  
 Uma mensagem suspeita é uma mensagem que excedeu o número máximo de tentativas de entrega para o aplicativo receptor. Essa situação pode surgir quando um aplicativo que lê uma mensagem de uma fila transacional não é possível processar a mensagem imediatamente devido a erros. Se o aplicativo anula a transação na qual a mensagem na fila foi recebida, ele retorna a mensagem à fila. Em seguida, o aplicativo tenta recuperar a mensagem novamente em uma nova transação. Se o problema que causou o erro não for corrigido, o aplicativo receptor pode preso em um loop de recebimento e anule a mesma mensagem até que ele excede o número máximo de tentativas de entrega e resultados de uma mensagem suspeita.  
  
 As principais diferenças entre o enfileiramento de mensagens (MSMQ) em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] que são relevantes para tratamento suspeita incluem o seguinte:  
  
-   O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta subfilas, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não oferecem suporte a subfilas. Subfilas são usadas no tratamento de mensagens suspeitas. As filas de repetição e a fila de suspeita são as subfilas para a fila de aplicativo que é criado com base nas configurações de manipulação de mensagens suspeitas. O `MaxRetryCycles` determina quantas Repita subfilas para criar. Portanto, quando executado em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` são ignorados e `ReceiveErrorHandling.Move` não é permitido.  
  
-   O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta negativo confirmação, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não. Uma confirmação negativa do Gerenciador de fila de recebimento faz com que o Gerenciador de fila de envio colocar a mensagem rejeitada na fila de mensagens mortas. Como tal, `ReceiveErrorHandling.Reject` não é permitido com [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a uma propriedade de mensagem que mantém uma contagem do número de tempos de entrega de mensagens é tentada. Essa propriedade de contagem de anulação não está disponível em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]mantém a contagem de anulação na memória, portanto, é possível que essa propriedade não pode conter um valor exato quando a mesma mensagem é lida por mais de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em uma Web farm.  
  
## <a name="remote-transactional-read"></a>Leitura transacional remota  
 MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a leituras transacionais remotas. Isso permite que um aplicativo que está lendo de uma fila para ser hospedado em um computador diferente do computador no qual a fila está hospedada. Isso garante a capacidade de ter um farm de serviços de leitura de uma fila central, o que aumenta a produtividade geral do sistema. Ele também garante que, se ocorrer uma falha ao ler e processar a mensagem, a transação será revertida e a mensagem permanece na fila para processamento posterior.  
  
## <a name="see-also"></a>Consulte também  
 [Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
