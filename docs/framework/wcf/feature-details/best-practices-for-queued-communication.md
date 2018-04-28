---
title: Práticas recomendadas para comunicação em fila
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
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 082fa083dbba601cefc00e40bad7b91e14a45d44
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="best-practices-for-queued-communication"></a>Práticas recomendadas para comunicação em fila
Este tópico fornece as práticas recomendadas para comunicação em fila em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. As seções a seguir discutem práticas recomendadas de uma perspectiva de cenário.  
  
## <a name="fast-best-effort-queued-messaging"></a>Rápido e melhor esforço enfileiradas mensagens  
 Para cenários que exigem a separação na fila de mensagens fornece e rápida, alto desempenho mensagens com garantia de melhor esforço, use uma fila não transacional e configure o <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> propriedade `false`.  
  
 Além disso, você pode optar por não incorrer em custos de gravações de disco, definindo o <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> propriedade `false`.  
  
 Segurança tem implicações no desempenho. Para obter mais informações, consulte [considerações sobre desempenho](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Ponta a ponta confiável na fila de mensagens  
 As seções a seguir descrevem as práticas recomendadas para cenários que exigem o sistema de mensagens confiável de ponta a ponta.  
  
### <a name="basic-reliable-transfer"></a>Transferência segura básico  
 Para a confiabilidade de ponta a ponta, defina o <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> propriedade `true` para garantir a transferência. O <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> propriedade pode ser definida como `true` ou `false` dependendo dos seus requisitos (o padrão é `true`). Em geral, o <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> está definida como `true` como parte da confiabilidade de ponta a ponta. O comprometimento é um custo de desempenho, mas faz com que a mensagem durável para que a mensagem não será perdida se um Gerenciador de fila falhar.  
  
### <a name="use-of-transactions"></a>Uso de transações  
 Você deve usar transações para garantir a segurança de ponta a ponta. `ExactlyOnce` GARANTIAS apenas certifique-se de que as mensagens são entregues para a fila de destino. Para garantir que a mensagem é recebida, use transações. Sem transações, se o serviço falhar, você perderá a mensagem que está sendo entregue, mas é entregue ao aplicativo.  
  
### <a name="use-of-dead-letter-queues"></a>Uso de filas de mensagens mortas  
 Filas de mensagens mortas Certifique-se de que você será notificado se uma mensagem de falha deve ser entregue para a fila de destino. Você pode usar a fila de mensagens mortas fornecido pelo sistema ou uma fila de mensagens mortas personalizada. Em geral, usar uma fila de mensagens mortas personalizada é recomendada porque ela permite que você envie mensagens de inatividade de um aplicativo em uma única fila de mensagens mortas. Caso contrário, todas as mensagens de inatividade que ocorrem para todos os aplicativos em execução no sistema são entregues a uma única fila. Cada aplicativo deve pesquisar se a fila de mensagens mortas para localizar as mensagens mortas que são relevantes para esse aplicativo. Às vezes, uma fila de mensagens mortas personalizada não for possível usar, por exemplo, ao usar o MSMQ 3.0.  
  
 Não é recomendável desativar filas de mensagens mortas para comunicação confiável de ponta a ponta.  
  
 Para obter mais informações, consulte [usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Uso da manipulação de mensagens suspeitas  
 Tratamento de mensagens suspeitas fornece a capacidade de se recuperar da falha para processar mensagens.  
  
 Ao usar o recurso de manipulação de mensagens suspeitas, certifique-se de que o <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> propriedade é definida como o valor apropriado. Definindo-a como <xref:System.ServiceModel.ReceiveErrorHandling.Drop> significa que os dados serão perdidos. Por outro lado, definindo-a como <xref:System.ServiceModel.ReceiveErrorHandling.Fault> falhas de host do serviço quando ele detecta uma mensagem suspeita. Usando o MSMQ 3.0, <xref:System.ServiceModel.ReceiveErrorHandling.Fault> é a melhor opção para evitar a perda de dados e mover a mensagem suspeita do caminho. Usando o MSMQ 4.0, <xref:System.ServiceModel.ReceiveErrorHandling.Move> é a abordagem recomendada. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Move uma mensagem inviabilizada fora da fila para que o serviço possa continuar a processar novas mensagens. O serviço de mensagens suspeitas pode processar a mensagem suspeita separadamente.  
  
 Para obter mais informações, consulte [manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Para alcançar alta taxa de transferência  
 Para obter alta taxa de transferência em um único ponto de extremidade, use o seguinte:  
  
-   Envio em lote transacionado. O lote transacionado garante que muitas mensagens podem ser lidas em uma única transação. Isso otimiza a transação é confirmada, aumentando o desempenho geral. O custo de processamento em lotes é que, se ocorrer uma falha em uma única mensagem em um lote, o lote inteiro será revertido e as mensagens devem ser processados um de cada vez até que seja seguro para o lote novamente. Na maioria dos casos, as mensagens suspeitas são raras, para que envio em lote é a melhor maneira de aumentar o desempenho, especialmente quando você tem outros gerenciadores de recursos que participam da transação. Para obter mais informações, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Simultaneidade. Simultaneidade aumenta a taxa de transferência, mas simultaneidade também afeta a contenção para recursos compartilhados. Para obter mais informações, consulte [simultaneidade](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Limitação. Para otimizar o desempenho, limitar o número de mensagens no pipeline dispatcher. Para obter um exemplo de como fazer isso, consulte [limitação](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Ao usar o envio em lote, lembre-se de limitação e simultaneidade traduzam a lotes simultâneos.  
  
 Para obter maior taxa de transferência e disponibilidade, use um farm de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços leem da fila. Isso exige que todos esses serviços de exponham o mesmo contrato no mesmo ponto de extremidade. A abordagem de farm funciona melhor para aplicativos com taxas de produção alto de mensagens porque ela permite que um número de serviços para todos os leiam a mesma fila.  
  
 Ao usar farms de servidores, lembre-se de que o MSMQ 3.0 não oferece suporte remotas leituras transacionadas. MSMQ 4.0 oferece suporte remotas leituras transacionadas.  
  
 Para obter mais informações, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) e [diferenças nos recursos de enfileiramento de mensagens no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Enfileiramento de mensagens com a unidade de trabalho semântica  
 Em alguns cenários de um grupo de mensagens em uma fila pode estar relacionado e, portanto, a ordem dessas mensagens é significativa. Nesses cenários, processar um grupo de mensagens relacionadas juntos como uma única unidade: todas as mensagens são processadas com êxito ou nenhuma está. Para implementar esse comportamento, use sessões com filas.  
  
 Para obter mais informações, consulte [mensagens na fila de agrupamento em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Correlação de mensagens de solicitação-resposta  
 Embora as filas são normalmente unidirecionais, em alguns cenários, que talvez você queira correlacionar uma resposta recebida para uma solicitação enviada anteriormente. Se você precisar de correlação, é recomendável que você aplique seu próprio cabeçalho de mensagem SOAP que contém informações de correlação com a mensagem. Normalmente, o remetente anexa esse cabeçalho com a mensagem e o destinatário, ao processar a mensagem e resposta com uma nova mensagem em uma fila de resposta, anexa o cabeçalho da mensagem do remetente que contém as informações de correlação para que o remetente pode identificar a mensagem de resposta com a mensagem de solicitação.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integração com aplicativos não WCF  
 Use `MsmqIntegrationBinding` ao integrar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços ou clientes com não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços ou clientes. Não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo pode ser um aplicativo de MSMQ escrito usando System. Messaging, COM+, Visual Basic ou C++.  
  
 Ao usar `MsmqIntegrationBinding`, lembre-se das seguintes opções:  
  
-   Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] corpo da mensagem não é igual um corpo de mensagem do MSMQ. Ao enviar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando uma associação enfileirada, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] corpo da mensagem é colocado dentro de uma mensagem MSMQ. A infraestrutura do MSMQ é indiferente a esta informação adicional. ele vê apenas a mensagem do MSMQ.  
  
-   `MsmqIntegrationBinding` oferece suporte a tipos de serialização populares. Com base no tipo de serialização, o tipo do corpo da mensagem genérica, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, usa os parâmetros de tipo diferente. Por exemplo, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> requer `MsmqMessage\<byte[]>` e <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> requer `MsmqMessage<Stream>`.  
  
-   Com a serialização de XML, você pode especificar o tipo conhecido usando o `KnownTypes` atributo no [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento que é usado para determinar como desserializar a mensagem XML.  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Agrupamento de mensagens em fila em uma sessão](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [Mensagens em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [Usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Diferenças de recursos da Fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Protegendo mensagens usando a segurança do transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Protegendo as mensagens com segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [Solução de problemas de mensagens em fila](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
