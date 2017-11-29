---
title: Manuseio de mensagem suspeita
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 719210e91fc98c7ceb0f6c51252cfcdfe2f1339c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="poison-message-handling"></a>Manuseio de mensagem suspeita
Um *mensagem suspeita* é uma mensagem que excedeu o número máximo de tentativas de entrega para o aplicativo. Essa situação pode ocorrer quando um aplicativo baseado em fila não é possível processar uma mensagem devido a erros. Para atender às demandas de confiabilidade, um aplicativo em fila recebe mensagens em uma transação. Anulando a transação na qual foi recebida uma mensagem na fila deixa a mensagem na fila para que a mensagem é repetida em uma nova transação. Se o problema que causou a anulação da transação não for corrigido, o aplicativo receptor pode preso em um loop de recebimento e anule a mesma mensagem até que o número máximo de tentativas de entrega foi excedido e resultados de uma mensagem suspeita.  
  
 Uma mensagem pode se tornar uma mensagem suspeita por vários motivos. As razões mais comuns são específicos do aplicativo. Por exemplo, se um aplicativo lê uma mensagem de uma fila e executa algum processamento do banco de dados, o aplicativo pode falhar ao obter um bloqueio no banco de dados, fazendo com que ele anular a transação. Como a transação de banco de dados foi anulada, a mensagem permanece na fila, que faz com que o aplicativo reler a mensagem uma segunda vez e fazer outra tentativa para adquirir um bloqueio no banco de dados. As mensagens também podem se tornar suspeitas se eles contêm informações inválidas. Por exemplo, uma ordem de compra pode conter um número inválido de cliente. Nesses casos, o aplicativo pode anular a transação voluntariamente e forçar a mensagem se torne uma mensagem suspeita.  
  
 Em raras ocasiões, as mensagens podem não expedidas para o aplicativo. O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] camada pode encontrar um problema com a mensagem, como se a mensagem tem o quadro errado, as credenciais de mensagem inválido anexado a ele ou um cabeçalho de ação inválida. Nesses casos, o aplicativo nunca recebe a mensagem. No entanto, a mensagem ainda pode se tornar uma mensagem suspeita e ser processada manualmente.  
  
## <a name="handling-poison-messages"></a>Como manipular mensagens suspeitas  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], suspeitas a manipulação de mensagens fornece um mecanismo para um aplicativo de recebimento lidar com todas as mensagens não podem ser enviadas para o aplicativo ou mensagens que são enviadas para o aplicativo, mas que não consiga ser processado porque razões específicas do aplicativo. Manipulação de mensagens suspeitas está configurada, as propriedades a seguir em cada uma das associações em fila disponíveis:  
  
-   `ReceiveRetryCount`. Um valor inteiro que indica o número máximo de tentativas de entrega de uma mensagem da fila de aplicativos para o aplicativo. O valor padrão é 5. Isso é suficiente para casos em que uma repetição imediatas corrige o problema, como com um deadlock temporário em um banco de dados.  
  
-   `MaxRetryCycles`. Um valor inteiro que indica o número máximo de ciclos de repetição. Consiste em um ciclo de repetição de transferência para a subfila de nova tentativa e, após um intervalo configurável, da subfila de nova tentativa de volta para a fila de aplicativo, tente novamente a entrega de uma mensagem da fila de aplicativos. O valor padrão é 2. Em [!INCLUDE[wv](../../../../includes/wv-md.md)], a mensagem é tentada máximo (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) vezes. `MaxRetryCycles`é ignorado em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. O tempo de espera entre os ciclos de repetição. O valor padrão é 30 minutos. `MaxRetryCycles`e `RetryCycleDelay` juntos fornecem um mecanismo para resolver o problema em que uma repetição após um intervalo periódico corrige o problema. Por exemplo, isso controla uma linha bloqueada definida no SQL Server pendentes de confirmação de transação.  
  
-   `ReceiveErrorHandling`. Uma enumeração que indica a ação a ser tomada para uma mensagem de falha na entrega depois que o número máximo de novas tentativas foi tentado. Os valores podem ser Fault, Drop, rejeitar e mover. A opção padrão é falha.  
  
-   Falha. Essa opção envia uma falha para o ouvinte que causou o `ServiceHost` à falha. A mensagem deve ser removida da fila de aplicativos por algum mecanismo externo antes que o aplicativo possa continuar a processar mensagens da fila.  
  
-   Descarte. Essa opção remove a mensagem suspeita e a mensagem nunca é enviada para o aplicativo. Se a mensagem `TimeToLive` propriedade expirou neste ponto, em seguida, a mensagem pode aparecer na fila de mensagens mortas do remetente. Caso contrário, a mensagem não aparece em qualquer lugar. Esta opção indica que o usuário não tiver especificado o que fazer se a mensagem for perdida.  
  
-   Rejeite. Essa opção está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Isso instrui o enfileiramento de mensagens (MSMQ) para enviar uma mensagem de confirmação negativa para o Gerenciador de fila de envio que o aplicativo não pode receber a mensagem. A mensagem é colocada na fila de mensagens mortas do Gerenciador de fila envio.  
  
-   Mova. Essa opção está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Isso move a mensagem suspeita para uma fila de mensagens suspeitas para processamento posterior por um aplicativo de tratamento de mensagens suspeitas. A fila de mensagens suspeitas é uma subfila da fila de aplicativo. Um aplicativo de tratamento de mensagens suspeitas pode ser um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que lê mensagens fora da fila de suspeita. A fila de suspeita é uma subfila da fila de aplicativo e podem ser tratada como net.msmq://\<*nome da máquina*>/*applicationQueue*; suspeitas, onde  *nome da máquina* é o nome do computador no qual reside a fila e o *applicationQueue* é o nome da fila específicas do aplicativo.  
  
 Esses são o número máximo de tentativas de entrega para uma mensagem:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) em [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Nenhuma tentativa é feita para uma mensagem que é entregue com êxito.  
  
 Para controlar o número de vezes que uma mensagem de leitura é tentada, [!INCLUDE[wv](../../../../includes/wv-md.md)] mantém uma propriedade de mensagem durável que conta o número de Anulações e uma propriedade de contagem de movimentação que conta o número de vezes que a mensagem se move entre a fila de aplicativos e subfilas. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal usa para calcular a contagem de repetições de recebimento e a contagem de ciclos de repetição. Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a contagem de anulação é mantida na memória, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de canal e é redefinido quando o aplicativo falhar. Além disso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal pode manter a anulação contagens de até 256 mensagens na memória a qualquer momento. Se uma mensagem 257th é lida, contagem de anulação da mensagem mais antigo é redefinida.  
  
 A anulação contagem e contagem propriedades estão disponíveis para a operação de serviço por meio do contexto de operação de mover. O exemplo de código a seguir mostra como acessá-los.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece duas associações na fila padrão:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. Um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] associação adequada para a execução de comunicação baseada em fila com outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Uma associação adequada para comunicação com aplicativos de enfileiramento de mensagens existentes.  
  
> [!NOTE]
>  Você pode alterar propriedades nessas associações com base nos requisitos da sua [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. A mensagem suspeita toda mecanismo de tratamento é local para o aplicativo de recebimento. O processo é invisível para o aplicativo de envio, a menos que o aplicativo de recebimento, por fim, para e envia uma confirmação negativa para o remetente. Nesse caso, a mensagem será movida para a fila de mensagens mortas do remetente.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Prática recomendada: Manipulação MsmqPoisonMessageException  
 Quando o serviço determina que uma mensagem é suspeita, transporte em fila lança um <xref:System.ServiceModel.MsmqPoisonMessageException> que contém o `LookupId` da mensagem suspeita.  
  
 Um aplicativo pode implementar o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface para tratar os erros que o aplicativo requer. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Controle estendido através de relatórios e tratamento de erro](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 O aplicativo pode exigir algum tipo de tratamento de mensagens suspeitas automatizado que move as mensagens suspeitas para uma fila de mensagens suspeitas para que o serviço pode acessar o restante das mensagens na fila. O único cenário para usar o mecanismo de manipulação de erros para escutar mensagens suspeitas exceções é quando o <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> configuração é definida como <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. O exemplo de mensagem de inviabilização do Message Queuing 3.0 demonstra esse comportamento. O exemplo a seguir descreve as etapas necessárias para tratar mensagens suspeitas, incluindo práticas recomendadas:  
  
1.  Certifique-se de que suas configurações suspeitas refletem os requisitos do seu aplicativo. Ao trabalhar com as configurações, certifique-se de que entendeu as diferenças entre os recursos do serviço de enfileiramento no [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2.  Se necessário, implemente o `IErrorHandler` para tratar erros de mensagens suspeitas. Como definir `ReceiveErrorHandling` para `Fault` requer um mecanismo manual para mover a mensagem suspeita fora da fila ou para corrigir um problema dependente externo, o uso típico é implementar `IErrorHandler` quando `ReceiveErrorHandling` é definido como `Fault`, como como mostrado no código a seguir.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  Criar um `PoisonBehaviorAttribute` que pode usar o comportamento de serviço. Instala o comportamento de `IErrorHandler` no dispatcher. Consulte o exemplo de código a seguir.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  Certifique-se de que o serviço é anotado com o atributo de comportamento suspeitas.  
  
  
  
 Além disso, se o `ReceiveErrorHandling` é definido como `Fault`, o `ServiceHost` Falha ao encontrar a mensagem suspeita. Você pode conectar a evento de falha e desligar o serviço, execute ações corretivas e reiniciar. Por exemplo, o `LookupId` no <xref:System.ServiceModel.MsmqPoisonMessageException> propagadas para o `IErrorHandler` pode ser observado e quando as falhas de host de serviço, você pode usar o `System.Messaging` API para receber a mensagem da fila usando o `LookupId` para remover a mensagem da fila e armazenar a mensagem em algum armazenamento externo ou outra fila. Você pode reiniciar `ServiceHost` para continuar o processamento normal. O [manipulação de mensagens suspeitas no MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) demonstra esse comportamento.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Tempo limite da transação e mensagens suspeitas  
 Uma classe de erros pode ocorrer entre o canal de transporte em fila e o código do usuário. Esses erros podem ser detectados por camadas intermediária, como a camada de segurança de mensagem ou o serviço de lógica de expedição. Por exemplo, um certificado x. 509 ausente detectado na camada de segurança de SOAP e uma ação ausente são casos em que a mensagem expedida para o aplicativo. Quando isso acontece, o modelo de serviço descartará a mensagem. Como a mensagem é lida em uma transação e um resultado para a transação não pode ser fornecido, a transação eventualmente expira, cancelamentos e a mensagem é colocada de volta na fila. Em outras palavras, para uma determinada classe de erros, a transação não anularão imediatamente mas aguarda até que a transação de tempo limite. Você pode modificar o tempo limite da transação para um serviço usando <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Para alterar o tempo limite da transação em uma base de todo o computador, modifique o arquivo Machine. config e defina o tempo limite de transação apropriado. É importante para observar que, dependendo do tempo limite definido na transação, a transação eventualmente anula e volta para a fila e sua contagem de anulação é incrementada. Finalmente, a mensagem se torna suspeita e a disposição da direita é feita de acordo com as configurações de usuário.  
  
## <a name="sessions-and-poison-messages"></a>Sessões e mensagens suspeitas  
 Uma sessão é submetido a repetição do mesmo e os procedimentos de tratamento de mensagens suspeitas como uma única mensagem. As propriedades listadas anteriormente para mensagens suspeitas se aplicam a toda a sessão. Isso significa que toda a sessão é repetida e vai para uma fila de mensagens suspeitas final ou fila de mensagens mortas do remetente se a mensagem foi rejeitada.  
  
## <a name="batching-and-poison-messages"></a>Mensagens suspeitas e envio em lote  
 Se uma mensagem se torna uma mensagem suspeita e é parte de um lote, em seguida, o lote inteiro será revertido e o canal retorna ao ler uma mensagem por vez. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]envio em lote, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Manipulação de mensagens em uma fila suspeita de mensagens suspeitas  
 Tratamento de mensagens suspeitas não termina quando uma mensagem é colocada na fila de mensagens suspeitas. Mensagens na fila de mensagens suspeitas ainda devem ser lidos e manipuladas. Você pode usar um subconjunto das configurações de manipulação de mensagens suspeitas durante a leitura de mensagens da subfila de inviabilização final. As configurações aplicáveis são `ReceiveRetryCount` e `ReceiveErrorHandling`. Você pode definir `ReceiveErrorHandling` Cancelar, rejeitar, ou de falha. `MaxRetryCycles`é ignorado e uma exceção será lançada se `ReceiveErrorHandling` está definido como Move.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 e Windows XP diferenças  
 Conforme observado anteriormente, nem todas as configurações de manipulação de mensagens suspeitas se aplicam a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Os seguintes principais diferenças entre o enfileiramento de mensagens em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], e [!INCLUDE[wv](../../../../includes/wv-md.md)] são relevantes para a manipulação de mensagens suspeitas:  
  
-   Mensagens do enfileiramento de mensagens em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta subfilas, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não oferecem suporte a subfilas. Subfilas são usadas no tratamento de mensagens suspeitas. As filas de repetição e a fila de suspeita são as subfilas para a fila de aplicativo que é criado com base nas configurações de manipulação de mensagens suspeitas. O `MaxRetryCycles` determina quantas Repita subfilas para criar. Portanto, quando executado em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` são ignorados e `ReceiveErrorHandling.Move` não é permitido.  
  
-   Mensagens do enfileiramento de mensagens em [!INCLUDE[wv](../../../../includes/wv-md.md)] suporta negativo confirmação, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não. Uma confirmação negativa do Gerenciador de fila de recebimento faz com que o Gerenciador de fila de envio colocar a mensagem rejeitada na fila de mensagens mortas. Como tal, `ReceiveErrorHandling.Reject` não é permitido com [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Mensagens do enfileiramento de mensagens em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a uma propriedade de mensagem que mantém uma contagem do número de tempos de entrega de mensagens é tentada. Essa propriedade de contagem de anulação não está disponível em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]mantém a contagem de anulação na memória, portanto, é possível que essa propriedade não pode conter um valor exato quando a mesma mensagem é lida por mais de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em um farm.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Diferenças de funcionalidades em fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Specifying and Handling Faults in Contracts and Services](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)
