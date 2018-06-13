---
title: Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: b70b7a7849ba0927c8ee4a4903aefc27bfa9d0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504075"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha
Mensagens em fila podem não entrega. Essas mensagens com falha são registradas em uma fila de mensagens mortas. Falha na entrega pode ser causado por motivos como falhas de rede, uma fila excluída, uma fila cheia, falha de autenticação ou uma falha ao entregar no tempo.  
  
 Mensagens em fila podem permanecer na fila por um longo tempo, se o aplicativo de recebimento não lê-los da fila de maneira oportuna. Esse comportamento pode não ser apropriado para mensagens de detecção de hora. Mensagens de detecção de hora têm um tempo para a propriedade de vida (TTL) definido na associação em fila, que indica quanto tempo as mensagens podem ficar na fila antes de expirarem. As mensagens expiradas são enviadas para uma fila especial chamada fila de mensagens mortas. As mensagens também podem ser colocadas em uma fila de mensagens mortas por outros motivos, como exceder uma cota de fila ou devido a falha de autenticação.  
  
 Em geral, os aplicativos gravar lógica de compensação para ler as mensagens da fila de mensagens mortas e razões da falha. A lógica de compensação depende da causa da falha. Por exemplo, no caso de falha de autenticação, você pode corrigir o certificado conectado com a mensagem e reenviar a mensagem. Se a entrega falhou porque a cota da fila de destino foi atingida, tente realizar novamente a entrega na esperança de que o problema de cota foi resolvido.  
  
 Sistemas de enfileiramento de mensagens mais tem uma fila de mensagens mortas de todo o sistema em que todas as mensagens com falha do sistema são armazenadas. Serviço de enfileiramento de mensagens (MSMQ) fornece duas filas de mensagens mortas de todo o sistema: uma fila de mensagens mortas transacional todo o sistema que armazena as mensagens que falharam na entrega à fila transacional e uma fila de mensagens mortas de todo o sistema não-transacional que armazena mensagens que falharam na entrega para a fila não transacional. Se dois clientes estão enviando mensagens para dois serviços diferentes e, portanto, diferentes filas no WCF estão compartilhando o mesmo serviço MSMQ para enviar, é possível ter uma mistura de mensagens na fila de mensagens mortas de sistema. Isso nem sempre é ideal. Em alguns casos (por exemplo, segurança), talvez não seja um cliente para ler mensagens de outro cliente de uma fila de mensagens mortas. Uma fila de mensagens mortas compartilhada também exige que os clientes navegar por meio de fila para localizar uma mensagem que eles enviaram, que pode ser extremamente dispendioso com base no número de mensagens na fila de mensagens mortas. Portanto, no WCF`NetMsmqBinding`, `MsmqIntegrationBinding,` e MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] fornecem uma fila de mensagens mortas personalizada (também conhecida como uma fila de mensagens mortas específicas do aplicativo).  
  
 A fila de mensagens mortas personalizada fornece isolamento entre os clientes que compartilham o mesmo serviço MSMQ para enviar mensagens.  
  
 Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], Windows Communication Foundation (WCF) fornece uma fila de mensagens mortas de todo o sistema para todos os aplicativos cliente em fila. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], WCF fornece uma fila de mensagens mortas para cada aplicativo cliente na fila.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Especificando o uso de fila de mensagens mortas  
 Uma fila de mensagens mortas é no Gerenciador de filas do aplicativo de envio. Ele armazena as mensagens que expiraram ou tiveram uma falha de transferência ou entrega.  
  
 A associação tem as seguintes propriedades de fila de mensagens mortas:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Lendo mensagens da fila de mensagens mortas  
 Um aplicativo que lê mensagens fora de uma fila de mensagens mortas é semelhante a um serviço WCF que lê a partir de uma fila de aplicativos, exceto as pequenas diferenças a seguir:  
  
-   Para ler mensagens de uma fila de mensagens mortas transacional do sistema, o identificador de recurso uniforme (URI) deve estar no formato: net.msmq://localhost/system$; DeadXact.  
  
-   Para ler mensagens de uma fila de mensagens mortas não transacional do sistema, o URI deve estar no formato: net.msmq://localhost/system$; mensagens mortas.  
  
-   Para ler mensagens de uma fila de mensagens mortas personalizada, o URI deve ser do formulário: net.msmq://localhost/private/\<*nome de dlq personalizada*> onde *nome de dlq personalizada* é o nome personalizado fila de mensagens mortas.  
  
 Para obter mais informações sobre como as filas de endereço, consulte [pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 A pilha do WCF no receptor faz a correspondência de endereços que o serviço está escutando com o endereço na mensagem. Se os endereços corresponderem, a mensagem é enviada; Caso contrário, a mensagem não é enviada. Isso pode causar problemas durante a leitura da fila de mensagens mortas, porque as mensagens na fila de mensagens mortas normalmente são endereçadas para o serviço e não o serviço de fila de mensagens mortas. Portanto, a leitura da fila de mensagens mortas do serviço deve instalar um filtro de endereço `ServiceBehavior` que instrui a pilha para corresponder a todas as mensagens na fila, independentemente do destinatário. Especificamente, você deve adicionar um `ServiceBehavior` com o <xref:System.ServiceModel.AddressFilterMode.Any> parâmetro para o serviço de leitura de mensagens da fila de mensagens mortas.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Tratamento de fila de mensagens mortas de mensagens suspeitas  
 Manipulação de mensagens suspeitas está disponível em filas de mensagens mortas, com algumas condições. Porque você não pode criar subfilas de filas do sistema, durante a leitura da fila de mensagens mortas de sistema, o `ReceiveErrorHandling` não pode ser definido como `Move`. Observe que, se você estiver lendo de uma fila de mensagens mortas personalizada, você pode ter subfilas e, portanto, `Move` é uma disposição válida para a mensagem suspeita.  
  
 Quando `ReceiveErrorHandling` é definido como `Reject`, quando a leitura da fila de mensagens mortas personalizada, a mensagem suspeita é colocada na fila de mensagens mortas de sistema. Se ler da fila de mensagens mortas de sistema, a mensagem será descartada (limpas). Uma rejeição de uma fila de mensagens mortas sistema em MSMQ descarta (limpa) a mensagem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar uma fila de mensagens mortas e como usá-lo para processar as mensagens expiradas. O exemplo é baseado no exemplo [como: mensagens na fila do Exchange com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). O exemplo a seguir mostra como escrever o código do cliente para o serviço que usa uma fila de mensagens mortas para cada aplicativo de processamento de pedidos. O exemplo também mostra como processar mensagens da fila de mensagens mortas.  
  
 A seguir está o código para um cliente que especifica uma fila de mensagens mortas para cada aplicativo.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 A seguir está o código para o arquivo de configuração do cliente.  
  
  
  
 A seguir está o código para um serviço de processamento de mensagens de uma fila de mensagens mortas.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 A seguir está o código para o arquivo de configuração do serviço de fila de mensagens mortas.  
  
  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
