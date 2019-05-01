---
title: Manuseio de mensagem suspeita
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: fe748ac40f03ed22cacb254ab464a6caf3d27a8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046431"
---
# <a name="poison-message-handling"></a>Manuseio de mensagem suspeita
Um *de mensagens suspeitas* é uma mensagem que foi excedido o número máximo de tentativas de entrega para o aplicativo. Essa situação pode ocorrer quando um aplicativo baseado em fila não pode processar uma mensagem devido a erros. Para atender às demandas de confiabilidade, um aplicativo na fila recebe mensagens em uma transação. Anulando a transação na qual uma mensagem na fila foi recebida deixa a mensagem na fila para que a mensagem é repetida em uma nova transação. Se o problema que causou a anulação da transação não for corrigido, o aplicativo de recebimento pode fique preso em um loop de recebimento e anulando a mesma mensagem até que o número máximo de tentativas de entrega foi excedido e resultados de uma mensagem suspeita.  
  
 Uma mensagem pode se tornar uma mensagem suspeita por vários motivos. Os motivos mais comuns são específicos do aplicativo. Por exemplo, se um aplicativo lê uma mensagem de uma fila e executa algum processamento do banco de dados, o aplicativo pode falhar obter um bloqueio no banco de dados, fazendo com que ele anular a transação. Porque a transação de banco de dados foi anulada, a mensagem permanecerá na fila, que faz com que o aplicativo releia a mensagem uma segunda vez e fazer outra tentativa para adquirir um bloqueio no banco de dados. As mensagens também podem se tornar suspeitas se eles contiverem informações inválidas. Por exemplo, uma ordem de compra pode conter um número inválido de cliente. Nesses casos, o aplicativo pode anular a transação voluntariamente e forçar a mensagem se torne uma mensagem suspeita.  
  
 Em raras ocasiões, as mensagens podem falhar ao expedidas para o aplicativo. A camada do Windows Communication Foundation (WCF) encontrar um problema com a mensagem, como se a mensagem tiver o quadro errado, as credenciais de mensagem inválido anexado a ele ou um cabeçalho de ação inválida. Nesses casos, o aplicativo nunca recebe a mensagem; No entanto, a mensagem ainda pode se tornar uma mensagem suspeita e ser processada manualmente.  
  
## <a name="handling-poison-messages"></a>Manipular mensagens suspeitas  
 No WCF, manipulação de mensagens suspeitas fornece um mecanismo para um aplicativo de recebimento lidar com mensagens que não podem ser expedidas para o aplicativo ou mensagens que são expedidos para o aplicativo, mas que não conseguirem ser processadas por causa de específicos do aplicativo motivos. Manipulação de mensagens suspeitas está configurada pelas seguintes propriedades em cada uma das associações em fila disponíveis:  
  
- `ReceiveRetryCount`. Um valor inteiro que indica o número máximo de tentativas de entrega de uma mensagem da fila de aplicativos para o aplicativo. O valor padrão é 5. Isso é suficiente em casos em que uma repetição imediata corrige o problema, como com um deadlock temporário em um banco de dados.  
  
- `MaxRetryCycles`. Um valor inteiro que indica o número máximo de ciclos de repetição. Um ciclo de repetição consiste em transferir uma mensagem da fila de aplicativos para a subfila de repetição e, após um intervalo configurável, da subfila de mensagens de repetição volta para a fila de aplicativos tentarão novamente a entrega. O valor padrão é 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], a mensagem é tentada um máximo de (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) vezes. `MaxRetryCycles` é ignorado em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- `RetryCycleDelay`. O tempo de espera entre os ciclos de repetição. O valor padrão é 30 minutos. `MaxRetryCycles` e `RetryCycleDelay` juntos fornecem um mecanismo para resolver o problema em que uma repetição após um intervalo periódico corrige o problema. Por exemplo, isso lida com uma linha bloqueada definida no SQL Server pendentes confirmação da transação.  
  
- `ReceiveErrorHandling`. Uma enumeração que indica a ação a tomar para uma mensagem que falha na entrega depois que o número máximo de repetições foi tentado. Os valores podem ser falhas, Drop, rejeitar e mover. A opção padrão é falha.  
  
- Falha. Essa opção envia uma falha para o ouvinte que causou o `ServiceHost` à falha. A mensagem deve ser removida da fila de aplicativos por algum mecanismo externo antes que o aplicativo possa continuar a processar mensagens da fila.  
  
- Descarte. Essa opção descarta a mensagem suspeita e a mensagem nunca é entregue ao aplicativo. Se a mensagem `TimeToLive` propriedade tiver expirado neste ponto, em seguida, a mensagem pode aparecer na fila de mensagens mortas do remetente. Caso contrário, a mensagem não aparecerá em lugar nenhum. Esta opção indica que o usuário não tiver especificado o que fazer se a mensagem será perdida.  
  
- Rejeite. Essa opção está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Isso instrui o enfileiramento de mensagens (MSMQ) para enviar uma confirmação negativa de volta para o Gerenciador de fila de envio que o aplicativo não pode receber a mensagem. A mensagem é colocada na fila de inatividade do Gerenciador de fila envio.  
  
- Mova. Essa opção está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Isso move a mensagem suspeita para uma fila de mensagens suspeitas para processamento posterior por um aplicativo de tratamento de mensagens suspeitas. A fila de mensagens suspeitas é uma subfila da fila de aplicativos. Um aplicativo de tratamento de mensagens suspeitas pode ser um serviço WCF que lê mensagens de fila de mensagens suspeitas. Fila de mensagens suspeitas é uma subfila da fila de aplicativos e podem ser tratada como net.msmq://\<*nome da máquina*>/*applicationQueue*; suspeitas, onde  *nome da máquina* é o nome do computador no qual reside a fila e o *applicationQueue* é o nome da fila específica do aplicativo.  
  
 A seguir estão o número máximo de tentativas da entrega feita para uma mensagem:  
  
- ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) em [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
- (ReceiveRetryCount + 1) no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Sem novas tentativas são feitas para uma mensagem que é entregue com êxito.  
  
 Para controlar o número de vezes que uma mensagem de leitura for tentada, [!INCLUDE[wv](../../../../includes/wv-md.md)] mantém uma propriedade de mensagem durável que conta o número de Anulações e uma propriedade de contagem de movimentação que conta o número de vezes que a mensagem se movem entre a fila de aplicativos e subfilas. O canal do WCF usa estes para calcular a contagem de repetição de recebimento e a contagem de ciclos de repetição. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a contagem de anulação é mantida na memória pelo canal do WCF e é redefinida quando o aplicativo falhar. Além disso, o canal do WCF pode manter que contagens de anulação de até 256 mensagens na memória a qualquer momento. Se uma mensagem 257th é lida, contagem de anulação da mensagem mais antigo será redefinida.  
  
 A anulação de contagem e contagem de propriedades estão disponíveis para a operação de serviço por meio do contexto da operação de mover. O exemplo de código a seguir mostra como acessá-los.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 O WCF fornece duas ligações na fila padrão:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] associação adequada para a execução de comunicação baseada em fila com outros pontos de extremidade do WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Uma associação adequada para se comunicar com aplicativos de enfileiramento de mensagens existentes.  
  
> [!NOTE]
>  Você pode alterar propriedades nessas associações de acordo com as necessidades do seu serviço WCF. A mensagem suspeita toda mecanismo de tratamento é local para o aplicativo de recebimento. O processo é invisível para o aplicativo de envio, a menos que o aplicativo de recebimento, por fim, interrompe e envia uma confirmação negativa volta ao remetente. Nesse caso, a mensagem é movida para a fila de mensagens mortas do remetente.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Prática recomendada: Tratamento de MsmqPoisonMessageException  
 Quando o serviço determina que uma mensagem é suspeita, transporte enfileirado lança um <xref:System.ServiceModel.MsmqPoisonMessageException> que contém o `LookupId` da mensagem suspeita.  
  
 Um aplicativo de recebimento pode implementar o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface para tratar os erros que o aplicativo requer. Para obter mais informações, consulte [estendendo o controle sobre o tratamento de erros e emissão de relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 O aplicativo pode exigir algum tipo de manipulação de mensagens suspeitas automatizado que move as mensagens suspeitas em uma fila de mensagens suspeitas, para que o serviço possa acessar o restante das mensagens na fila. O único cenário para usar o mecanismo do manipulador de erro para escutar mensagens suspeitas exceções é quando o <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> configuração é definida como <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. O exemplo de mensagens suspeitas para enfileiramento de mensagens 3.0 demonstra esse comportamento. O exemplo a seguir descreve as etapas necessárias para tratar mensagens suspeitas, incluindo práticas recomendadas:  
  
1. Certifique-se de que suas configurações suspeitas refletem os requisitos do seu aplicativo. Ao trabalhar com as configurações, certifique-se de que você entenda as diferenças entre os recursos do enfileiramento de mensagens em [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. Se necessário, implemente o `IErrorHandler` para lidar com erros de mensagens suspeitas. Como definir `ReceiveErrorHandling` para `Fault` requer um mecanismo manual para mover a mensagem suspeita fora da fila ou para corrigir um problema de dependente externo, o uso típico é implementar `IErrorHandler` quando `ReceiveErrorHandling` é definido como `Fault`, como como mostrado no código a seguir.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Criar um `PoisonBehaviorAttribute` que o comportamento de serviço pode usar. Instala o comportamento de `IErrorHandler` no dispatcher. Consulte o exemplo de código a seguir.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Certifique-se de que seu serviço é anotado com o atributo de comportamento suspeitos.  

 Além disso, se o `ReceiveErrorHandling` é definido como `Fault`, o `ServiceHost` Falha ao encontrar a mensagem suspeita. Você pode interligar o evento com falha e desligar o serviço, tome medidas corretivas e reiniciar. Por exemplo, o `LookupId` no <xref:System.ServiceModel.MsmqPoisonMessageException> propagadas para o `IErrorHandler` pode ser observado e quando as falhas de host de serviço, você pode usar o `System.Messaging` API para receber a mensagem de fila usando o `LookupId` para remover a mensagem da fila e armazenar a mensagem em algum armazenamento externo ou outra fila. Você pode reiniciar `ServiceHost` para continuar o processamento normal. O [manipulação de mensagens suspeitas no MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) demonstra esse comportamento.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Tempo limite da transação e mensagens suspeitas  
 Uma classe de erros pode ocorrer entre o canal de transporte em fila e o código do usuário. Esses erros podem ser detectados por camadas intermediária, como a camada de segurança de mensagem ou o serviço de lógica de expedição. Por exemplo, um certificado x. 509 ausente detectado na camada de segurança de SOAP e uma ação ausente são casos em que a mensagem expedida para o aplicativo. Quando isso acontece, o modelo de serviço descarta a mensagem. Como a mensagem é lida em uma transação e um resultado para essa transação não pode ser fornecido, a transação eventualmente expira, anulações e a mensagem é colocada de volta na fila. Em outras palavras, para uma determinada classe de erros, a transação não anular imediatamente, mas aguarda até que a transação de tempo limite. Você pode modificar o tempo limite da transação para um serviço usando <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Para alterar o tempo limite da transação em todo o computador, modifique o arquivo Machine. config e defina o tempo limite de transação adequado. É importante para observar que, dependendo do tempo limite definido na transação, a transação, eventualmente, anula e volta para a fila e sua contagem de anulação é incrementada. Finalmente, a mensagem se torna suspeita e a disposição da direita é feita de acordo com as configurações de usuário.  
  
## <a name="sessions-and-poison-messages"></a>Sessões e mensagens suspeitas  
 Uma sessão sofre a repetição do mesma e os procedimentos de manipulação de mensagens suspeitas como uma única mensagem. As propriedades listadas anteriormente para mensagens suspeitas se aplicam a toda a sessão. Isso significa que toda a sessão é repetida e vai para uma fila de mensagens suspeitas final ou fila de mensagens mortas do remetente, se a mensagem será rejeitada.  
  
## <a name="batching-and-poison-messages"></a>Mensagens suspeitas e envio em lote  
 Se uma mensagem se torna uma mensagem suspeita e é parte de um lote, em seguida, o lote inteiro será revertido e o canal retorna ao ler uma mensagem por vez. Para obter mais informações sobre o envio em lote, consulte [mensagens de envio em lote em uma transação](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Manipulação de mensagens em uma fila de mensagens suspeitas de mensagens suspeitas  
 Manipulação de mensagens suspeitas não termina quando uma mensagem é colocada na fila de mensagens suspeitas. Mensagens na fila de mensagens suspeitas ainda devem ser lidas e manipuladas. Ao ler as mensagens da subfila de mensagens suspeita final, você pode usar um subconjunto das configurações de manipulação de mensagens suspeitas. As configurações aplicáveis são `ReceiveRetryCount` e `ReceiveErrorHandling`. Você pode definir `ReceiveErrorHandling` para soltar, rejeitar, ou de falha. `MaxRetryCycles` é ignorado e uma exceção é lançada se `ReceiveErrorHandling` é definido como a movimentação.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Diferenças do Windows XP, Windows Server 2003 e Windows Vista  
 Conforme observado anteriormente, nem todas as configurações de manipulação de mensagens suspeitas se aplicam a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. A seguir as principais diferenças entre o enfileiramento de mensagens em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], e [!INCLUDE[wv](../../../../includes/wv-md.md)] são relevantes para a manipulação de mensagens suspeitas:  
  
- Mensagem de enfileiramento de mensagens no [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a subfilas, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não dão suporte a subfilas. Subfilas são usadas na manipulação de mensagens suspeitas. As filas de repetição e a fila de mensagens suspeitas são as subfilas para a fila do aplicativo é criado com base nas configurações de manipulação de mensagens suspeitas. O `MaxRetryCycles` determina quantos repetir as subfilas para criar. Portanto, quando em execução no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` são ignorados e `ReceiveErrorHandling.Move` não é permitido.  
  
- Mensagem de enfileiramento de mensagens no [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a negativo confirmação, enquanto [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] não fizer isso. Uma confirmação negativa de Gerenciador de fila de recebimento faz com que o Gerenciador de fila de envio colocar a mensagem rejeitada na fila de inatividade. Como tal, `ReceiveErrorHandling.Reject` não é permitido com [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Mensagem de enfileiramento de mensagens em [!INCLUDE[wv](../../../../includes/wv-md.md)] dá suporte a uma propriedade de mensagem que mantém uma contagem do número de tempos de entrega de mensagens é tentada. Essa propriedade de contagem de anulação não está disponível no [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF mantém a contagem de anulação na memória, portanto, é possível que essa propriedade não pode conter um valor preciso quando a mesma mensagem é lida por mais de um serviço WCF em um farm.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de filas](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Diferenças de recursos da Fila no Windows Vista, Windows Server 2003 e Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Especificando e lidando com falhas em contratos e serviços](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
