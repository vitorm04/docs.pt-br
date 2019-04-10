---
title: Práticas recomendadas para comunicação em fila
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: 27b9c6e117b6ba809daae87d376b03e27bc2b0f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230090"
---
# <a name="best-practices-for-queued-communication"></a>Práticas recomendadas para comunicação em fila
Este tópico fornece as práticas recomendadas para a comunicação em fila no Windows Communication Foundation (WCF). As seções a seguir discutem as práticas recomendadas de uma perspectiva de cenário.  
  
## <a name="fast-best-effort-queued-messaging"></a>Rápido, melhor esforço na fila mensagens  
 Para cenários que exigem a separação na fila de mensagens fornece e rápida, alto desempenho, as mensagens com garantias de melhor esforço, use uma fila não transacional e defina as <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> propriedade para `false`.  
  
 Além disso, você pode optar por não incorrer em custos de gravações em disco, definindo o <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> propriedade para `false`.  
  
 Segurança tem implicações no desempenho. Para obter mais informações, consulte [considerações sobre desempenho](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Ponta a ponta confiável na fila de mensagens  
 As seções a seguir descrevem as práticas recomendadas para cenários que exigem o sistema de mensagens confiável de ponta a ponta.  
  
### <a name="basic-reliable-transfer"></a>Transferência confiável básica  
 Para obter confiabilidade de ponta a ponta, defina as <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> propriedade para `true` para garantir a transferência. O <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> propriedade pode ser definida como `true` ou `false` dependendo dos seus requisitos (o padrão é `true`). Em geral, o <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> estiver definida como `true` como parte da confiabilidade de ponta a ponta. O comprometimento é um custo de desempenho, mas torna a mensagem durável para que a mensagem não seja perdida em caso de falha de um Gerenciador de fila.  
  
### <a name="use-of-transactions"></a>Uso de transações  
 Você deve usar transações para garantir a confiabilidade de ponta a ponta. `ExactlyOnce` GARANTIAS apenas certifique-se de que as mensagens sejam entregues à fila de destino. Para garantir que a mensagem é recebida, use transações. Sem transações, se o serviço falhar, você perderá a mensagem que está sendo entregue, mas, na verdade, é entregue ao aplicativo.  
  
### <a name="use-of-dead-letter-queues"></a>Uso de filas  
 Filas de inatividade Certifique-se de que você será notificado se uma mensagem de falha sejam entregues à fila de destino. Você pode usar a fila de inatividade fornecido pelo sistema ou uma fila mortas personalizada. Em geral, usar uma fila de inatividade personalizada é melhor porque ela permite que você envie mensagens de inatividade de um aplicativo em uma única fila de inatividade. Caso contrário, todas as mensagens mortas que ocorrem para todos os aplicativos em execução no sistema são entregues para uma única fila. Cada aplicativo deve pesquisar no entanto a fila de inatividade para localizar as mensagens mortas que são relevantes para esse aplicativo. Às vezes, a usar uma fila de inatividade personalizada não é viável, como ao usar o MSMQ 3.0.  
  
 Não é recomendável desativar filas para comunicação confiável de ponta a ponta.  
  
 Para obter mais informações, consulte [usando filas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Uso de manipulação de mensagens suspeitas  
 Manipulação de mensagens suspeitas fornece a capacidade de recuperar de falhas para processar mensagens.  
  
 Ao usar o recurso de manipulação de mensagens suspeitas, certifique-se de que o <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> estiver definida como o valor apropriado. Configurando-a como <xref:System.ServiceModel.ReceiveErrorHandling.Drop> significa que os dados serão perdidos. Por outro lado, configurando-a como <xref:System.ServiceModel.ReceiveErrorHandling.Fault> de falhas de host de serviço quando ele detecta uma mensagem suspeita. Usando o MSMQ 3.0, <xref:System.ServiceModel.ReceiveErrorHandling.Fault> é a melhor opção para evitar a perda de dados e mover a mensagem suspeita fora do caminho. Usando o MSMQ 4.0, <xref:System.ServiceModel.ReceiveErrorHandling.Move> é a abordagem recomendada. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Move uma mensagem inviabilizada fora da fila para que o serviço possa continuar a processar novas mensagens. O serviço de mensagens suspeitas pode processar a mensagem suspeita separadamente.  
  
 Para obter mais informações, consulte [manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Alcança alto rendimento  
 Para obter alta taxa de transferência em um único ponto de extremidade, use o seguinte:  
  
-   Envio em lote transacionado. O lote transacionado garante que muitas mensagens podem ser lidos em uma única transação. Isso otimiza as confirmações de transações, aumentando o desempenho geral. O custo do envio em lote é que, se ocorrer uma falha em uma única mensagem dentro de um lote, em seguida, o lote inteiro será revertido e as mensagens devem ser processados um de cada vez até que seja seguro para o lote novamente. Na maioria dos casos, as mensagens suspeitas são raras, portanto, o envio em lote é a maneira preferencial para aumentar o desempenho do sistema, especialmente quando você tiver outros gerenciadores de recursos que participam da transação. Para obter mais informações, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Simultaneidade. Simultaneidade aumenta a taxa de transferência, mas a contenção para recursos compartilhados também afeta a simultaneidade. Para obter mais informações, consulte [simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   A limitação. Para otimizar o desempenho, limite o número de mensagens no pipeline do dispatcher. Para obter um exemplo de como fazer isso, consulte [limitação](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Ao usar o envio em lote, lembre-se de que a simultaneidade e a limitação convertem a lotes simultâneos.  
  
 Para obter maior taxa de transferência e disponibilidade, use um farm de serviços WCF que ler a fila. Isso requer que todos esses serviços expõem o mesmo contrato no mesmo ponto de extremidade. A abordagem de farm funciona melhor para aplicativos que têm taxas de produção alto de mensagens porque ela permite que um número de serviços para todos os ler da mesma fila.  
  
 Ao usar farms de servidores, lembre-se de que o MSMQ 3.0 não dá suporte a leituras transacionadas remotas. MSMQ 4.0 oferece suporte a leituras transacionadas remotas.  
  
 Para obter mais informações, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) e [diferenças nos recursos de enfileiramento de mensagens no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Enfileiramento de mensagens com a unidade de trabalho semântica  
 Em alguns cenários de um grupo de mensagens em uma fila pode estar relacionado e, portanto, a ordem dessas mensagens é significativa. Nesses cenários, processar um grupo de mensagens relacionadas juntas como uma única unidade: todas as mensagens são processadas com êxito ou nenhuma é. Para implementar esse comportamento, use as sessões com filas.  
  
 Para obter mais informações, consulte [mensagens na fila de agrupamento em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Correlacionar mensagens de solicitação-resposta  
 Embora as filas são normalmente unidirecionais, em alguns cenários, que talvez você queira correlacionar uma resposta recebida a uma solicitação enviada anteriormente. Se você precisar de correlação, é recomendável que você aplique a seu próprio cabeçalho de mensagem SOAP que contém informações de correlação com a mensagem. Normalmente, o remetente anexa esse cabeçalho com a mensagem e o receptor, após o processamento da mensagem e responder com uma nova mensagem em uma fila de resposta, anexa o cabeçalho da mensagem do remetente que contém as informações de correlação para que o remetente pode Identifique a mensagem de resposta com a mensagem de solicitação.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integração de aplicativos não WCF  
 Use `MsmqIntegrationBinding` ao integrar clientes ou serviços WCF com clientes ou serviços não WCF. O aplicativo não WCF pode ser um aplicativo de MSMQ gravado usando System. Messaging, COM+, Visual Basic ou C++.  
  
 Ao usar `MsmqIntegrationBinding`, esteja ciente das seguintes opções:  
  
-   Um corpo de mensagem do WCF não é igual a um corpo de mensagem do MSMQ. Ao enviar uma mensagem do WCF usando uma associação enfileirada, o corpo da mensagem do WCF é colocado dentro de uma mensagem MSMQ. A infraestrutura do MSMQ é alheia a essas informações extras; ele vê apenas a mensagem do MSMQ.  
  
-   `MsmqIntegrationBinding` dá suporte a tipos de serialização populares. Com base no tipo de serialização, o tipo do corpo da mensagem genérica, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, usa os parâmetros de tipo diferente. Por exemplo, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> requer `MsmqMessage\<byte[]>` e <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> requer `MsmqMessage<Stream>`.  
  
-   Com a serialização de XML, você pode especificar o tipo conhecido usando o `KnownTypes` atributo o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento que é usado para determinar como desserializar a mensagem XML.  
  
## <a name="see-also"></a>Consulte também

- [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Como: fazer intercâmbio de mensagens em fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Como: fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Agrupamento de mensagens em fila em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)
- [Mensagens de lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)
- [Utilizando filas de mensagens mortas para manuseio de transferência de mensagens com falha](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Manuseio de mensagem suspeita](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Diferenças de recursos em fila no Windows Vista, Windows Server 2003, e no Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Mensagens de segurança que usam a segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Protegendo as mensagens com a segurança de mensagens](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)
- [Mensagens em fila da solução de problemas](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
