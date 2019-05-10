---
title: Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: c83d48994c6038dfde67867a1766777c479c2169
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637727"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha
Mensagens em fila podem falhar de entrega. Essas mensagens com falha são registradas em uma fila de inatividade. Falha na entrega pode ser causado por motivos como falhas de rede, uma fila excluída, uma fila cheia, falha de autenticação ou uma falha ao entregar no prazo.  
  
 Mensagens em fila podem permanecer na fila por um longo tempo, se o aplicativo de recebimento não lê-los da fila no momento oportuno. Esse comportamento pode não ser apropriado para mensagens de detecção de hora. Mensagens de detecção de hora têm um tempo à propriedade de vida (TTL) definido na associação em fila, que indica quanto tempo as mensagens podem ser na fila antes de expirarem. As mensagens expiradas são enviadas para uma fila especial chamada a fila de inatividade. As mensagens também podem ser colocadas em uma fila de inatividade por outros motivos, como exceder uma cota de fila ou devido a falha de autenticação.  
  
 Em geral, aplicativos gravar a lógica de compensação para ler as mensagens da fila de inatividade e razões da falha. A lógica de compensação depende a causa da falha. Por exemplo, no caso de falha de autenticação, você pode corrigir o certificado anexado com a mensagem e reenviar a mensagem. Se a entrega falhou porque a cota da fila de destino foi atingida, tente realizar novamente a entrega na esperança de que o problema de cota foi resolvido.  
  
 Sistemas de enfileiramento de mensagens mais tem uma fila de inatividade em todo o sistema em que todas as mensagens com falha do sistema são armazenadas. Serviço de enfileiramento de mensagens (MSMQ) fornece duas filas de inatividade de todo o sistema: uma fila transacional de inatividade de todo o sistema que armazena as mensagens que falharam na entrega para a fila transacional e uma fila não transacional de inatividade de todo o sistema que armazena mensagens que falharam na entrega para a fila não transacional. Se dois clientes estão enviando mensagens para dois serviços diferentes e, portanto, diferentes filas no WCF estão compartilhando o mesmo serviço MSMQ para enviar, em seguida, é possível ter uma mistura de mensagens na fila de inatividade do sistema. Isso nem sempre é ideal. Em muitos casos (por exemplo, segurança), não convém ler mensagens do outro cliente de uma fila de inatividade de um cliente. Uma fila de inatividade compartilhada também requer que os clientes procurar por meio de fila para localizar uma mensagem de que eles enviaram, que pode ser proibitivo com base no número de mensagens na fila de inatividade. Portanto, no WCF`NetMsmqBinding`, `MsmqIntegrationBinding,` e o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] fornecem uma fila de inatividade personalizada (também conhecida como uma fila de inatividade específico do aplicativo).  
  
 A fila de inatividade personalizada fornece isolamento entre os clientes que compartilham o mesmo serviço MSMQ para enviar mensagens.  
  
 Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], Windows Communication Foundation (WCF) fornece uma fila de inatividade em todo o sistema para todos os aplicativos cliente na fila. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], o WCF fornece uma fila de inatividade para cada aplicativo cliente na fila.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Especificando o uso da fila de inatividade  
 Uma fila de inatividade é no Gerenciador de fila do aplicativo de envio. Ele armazena as mensagens que expiraram ou tiveram uma falha de transferência ou entrega.  
  
 A associação tem as seguintes propriedades de fila de inatividade:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Leitura de mensagens da fila de inatividade  
 Um aplicativo que lê mensagens fora de uma fila de inatividade é semelhante a um serviço WCF que lê de uma fila de aplicativos, exceto para as pequenas diferenças a seguir:  
  
- Para ler mensagens de uma fila mortas transacional do sistema, o identificador de recurso uniforme (URI) deve estar no formato: $ net.msmq://localhost/system; DeadXact.  
  
- Para ler mensagens de uma fila de inatividade não-transacional do sistema, o URI deve estar no formato: $ net.msmq://localhost/system; mensagens mortas.  
  
- Para ler mensagens de uma fila de inatividade personalizada, o URI deve ser de que o formulário: net.msmq://localhost/private/\<*dlq-personalizado-name*> onde *nome de personalizado dlq* é o nome de personalizado fila de inatividade.  
  
 Para obter mais informações sobre como as filas de endereço, consulte [pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 A pilha do WCF no receptor faz a correspondência de endereços que o serviço está escutando com o endereço na mensagem. Se os endereços corresponderem, a mensagem é enviada; Caso contrário, a mensagem não será enviada. Isso pode causar problemas durante a leitura da fila de inatividade, pois as mensagens na fila de inatividade são normalmente enviadas para o serviço e não o serviço de fila de inatividade. Portanto, o leitura da fila de inatividade do serviço deve instalar um filtro de endereço `ServiceBehavior` que instrui a pilha para corresponder a todas as mensagens na fila, independentemente do destinatário. Especificamente, você deve adicionar uma `ServiceBehavior` com o <xref:System.ServiceModel.AddressFilterMode.Any> parâmetro para o serviço de mensagens de leitura da fila de inatividade.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Tratamento da fila de inatividade de mensagens suspeitas  
 Manipulação de mensagens suspeitas está disponível em filas de inatividade, com algumas condições. Porque você não pode criar subfilas de filas do sistema durante a leitura da fila de inatividade do sistema, o `ReceiveErrorHandling` não pode ser definido como `Move`. Observe que, se você estiver lendo de uma fila de inatividade personalizada, você pode ter subfilas e, portanto, `Move` é um descarte válido para a mensagem suspeita.  
  
 Quando `ReceiveErrorHandling` é definido como `Reject`, quando a leitura da fila de mensagens mortas personalizada, a mensagem suspeita é colocada na fila de inatividade do sistema. Se ler a fila de inatividade do sistema, a mensagem é descartada (limpo). Uma rejeição de uma fila de inatividade do sistema em MSMQ descartes (limpa) a mensagem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar uma fila de inatividade e como usá-lo para processar as mensagens expiradas. O exemplo é baseado no exemplo em [como: Troca de mensagens com pontos de extremidade do WCF em fila](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). O exemplo a seguir mostra como escrever o código do cliente para o serviço que usa uma fila de inatividade para cada aplicativo de processamento de pedidos. O exemplo também mostra como processar as mensagens da fila de inatividade.  
  
 A seguir está o código para um cliente que especifica uma fila de inatividade para cada aplicativo.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 A seguir está o código para o arquivo de configuração do cliente.  

 A seguir está o código para um serviço de processamento de mensagens de uma fila de inatividade.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 A seguir está o código para o arquivo de configuração do serviço de fila de inatividade.  

## <a name="see-also"></a>Consulte também

- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Como: Troca de mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
