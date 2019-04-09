---
title: Diferenças de recursos em fila no Windows Vista, Windows Server 2003, e no Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: d13cb3e732d0276902def5de6ca7c007f61b0ec9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115980"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Diferenças de recursos em fila no Windows Vista, Windows Server 2003, e no Windows XP
Este tópico resume as diferenças entre o recurso de filas do Windows Communication Foundation (WCF) entre [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Fila de inatividade específico do aplicativo  
 Mensagens em fila podem permanecer na fila indefinidamente se o aplicativo de recebimento não lê-los de forma oportuna. Esse comportamento não é aconselhável se as mensagens são sensíveis ao tempo. Mensagens de detecção de hora têm um `TimeToLive` propriedade definida na associação em fila. Essa propriedade indica quanto tempo as mensagens podem ser na fila antes de expirarem. As mensagens expiradas são enviadas para uma fila especial chamada a fila de inatividade. Uma mensagem também pode terminar em uma fila de inatividade por outros motivos, como exceder uma cota de fila ou devido a uma falha de autenticação.  
  
 Normalmente, existe uma fila de inatividade de todo o sistema única para todos os aplicativos em fila que compartilham um Gerenciador de fila. Uma fila de inatividade para cada aplicativo permite melhor isolamento entre aplicativos em fila que compartilham um Gerenciador de fila, permitindo que esses aplicativos especificar sua própria fila de inatividade específicos do aplicativo. Tem um aplicativo que compartilha uma fila de inatividade com outros aplicativos procurar a fila para localizar as mensagens que se aplicam a ele. Com uma fila de inatividade específico do aplicativo, o aplicativo pode ter certeza de que todas as mensagens na fila de inatividade são aplicáveis a ele.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] fornece para filas de inatividade específico do aplicativo. Filas de inatividade específico do aplicativo não estão disponíveis no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], e os aplicativos devem usar a fila de inatividade em todo o sistema.  
  
## <a name="poison-message-handling"></a>Manipulação de mensagens suspeitas  
 Uma mensagem suspeita é uma mensagem que foi excedido o número máximo de tentativas de entrega para o aplicativo de recebimento. Essa situação pode ocorrer quando um aplicativo que lê uma mensagem de uma fila transacional não é possível processar a mensagem imediatamente devido a erros. Se o aplicativo anula a transação na qual a mensagem na fila foi recebida, ele retorna a mensagem à fila. Em seguida, o aplicativo tenta recuperar a mensagem novamente em uma nova transação. Se o problema que causa o erro não for corrigido, o aplicativo de recebimento pode fique preso em um loop de recebimento e anulando a mesma mensagem até que ele excede o número máximo de tentativas de entrega, bem como resultados de uma mensagem suspeita.  
  
 As principais diferenças entre o enfileiramento de mensagens (MSMQ) em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] que são relevantes para a manipulação de suspeita incluem o seguinte:  
  
-   MSMQ no [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a subfilas, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não dão suporte a subfilas. Subfilas são usadas na manipulação de mensagens suspeitas. As filas de repetição e a fila de mensagens suspeitas são as subfilas para a fila do aplicativo é criado com base nas configurações de manipulação de mensagens suspeitas. O `MaxRetryCycles` determina quantos repetir as subfilas para criar. Portanto, quando em execução no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` são ignorados e `ReceiveErrorHandling.Move` não é permitido.  
  
-   MSMQ no [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a negativo confirmação, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não fizer isso. Uma confirmação negativa de Gerenciador de fila de recebimento faz com que o Gerenciador de fila de envio colocar a mensagem rejeitada na fila de inatividade. Como tal, `ReceiveErrorHandling.Reject` não é permitido com [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   O MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a uma propriedade de mensagem que mantém uma contagem do número de tempos de entrega de mensagens é tentada. Essa propriedade de contagem de anulação não está disponível no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF mantém a contagem de anulação na memória, portanto, é possível que essa propriedade não pode conter um valor preciso quando a mesma mensagem é lida por mais de um serviço WCF em uma Web farm.  
  
## <a name="remote-transactional-read"></a>Leitura transacional remota  
 MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a leituras transacionais remotas. Isso permite que um aplicativo que está lendo de uma fila para ser hospedado em um computador diferente do computador no qual a fila está hospedada. Isso garante a capacidade de ter um farm de serviços de leitura de uma fila central, o que aumenta a produtividade geral do sistema. Ela também garante que, se ocorrer uma falha ao ler e processar a mensagem, a transação será revertida e a mensagem permanecerá na fila para processamento posterior.  
  
## <a name="see-also"></a>Consulte também

- [Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Manuseio de mensagem suspeita](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
