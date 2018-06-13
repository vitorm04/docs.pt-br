---
title: Enfileiramento no WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 7f0a6700dba8eb844cc471704095b29c2a2c7937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496478"
---
# <a name="queuing-in-wcf"></a>Enfileiramento no WCF
Esta seção descreve como usar a comunicação em fila no Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Associação de transporte de filas como um WCF  
 No WCF, os contratos de especificar o que está sendo trocado. Contratos são trocas de mensagens de aplicativo específico ou dependentes de negócios. O mecanismo usado para troca de mensagens (ou "como") é especificado nas associações. Associações do WCF encapsulam os detalhes de troca de mensagens. Eles expõem os botões de configuração para o usuário controlar vários aspectos do transporte ou o protocolo que representam as associações. Enfileiramento no WCF é tratado como qualquer outra transporte ligação, que é uma grande vantagem para muitos aplicativos de enfileiramento de mensagens. Atualmente, muitos aplicativos de enfileiramento de mensagens são gravados Diferentemente de outras chamadas de procedimento remoto (RPC)-estilo de aplicativos distribuídos, tornando mais difícil de seguir e manter. Com o WCF, o estilo de escrever um aplicativo distribuído é semelhante a, tornando mais fácil de seguir e manter. Além disso, Fatorando o mecanismo do exchange separadamente da lógica de negócios, é mais fácil de configurar o transporte ou fazer alterações sem afetar o código específico do aplicativo. A figura a seguir ilustra a estrutura de um serviço WCF e usar o MSMQ como um transporte de cliente.  
  
 ![Na fila de diagrama do aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Como você pode ver na figura anterior, o cliente e o serviço devem definir apenas a semântica do aplicativo, ou seja, o contrato e a implementação. O serviço define uma associação enfileirada com configurações preferenciais. O cliente usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um cliente WCF para o serviço e gere um arquivo de configuração que descreve as associações a ser usado para enviar mensagens para o serviço. Portanto, para enviar uma mensagem na fila, o cliente cria um cliente WCF e invoca uma operação sobre ele. Isso faz com que a mensagem ser enviada para a fila de transmissão e transferida para a fila de destino. Todas as complexidades de comunicação em fila estão ocultos do aplicativo que está enviando e recebendo mensagens.  
  
 Advertências sobre associação enfileirada no WCF incluem:  
  
-   Serviço todas as operações devem ser unidirecionais porque o padrão na fila de associação no WCF não oferece suporte à comunicação duplex usando filas. Um exemplo de comunicação bidirecional ([comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md)) ilustra como usar dois contratos unidirecionais para implementar o uso de filas de comunicação duplex.  
  
-   Para gerar um WCF cliente usando uma troca de metadados requer um ponto de extremidade HTTP adicional no serviço de forma que ela possa ser consultada diretamente para gerar o cliente do WCF e obter informações de associação para configurar adequadamente a comunicação em fila.  
  
-   Configuração adicional fora do WCF com base na associação em fila, é necessária. Por exemplo, a <xref:System.ServiceModel.NetMsmqBinding> classe que é fornecido com o WCF exige que você configure as ligações, bem como a configuração mínima de enfileiramento de mensagens (MSMQ).  
  
 As seções a seguir descrevem específicas na fila associações fornecidas com o WCF, que se baseiam em MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 O transporte em fila no WCF usa MSMQ para sua comunicação em fila.  
  
 MSMQ é fornecido como um componente opcional do Windows e é executado como um serviço NT. Captura as mensagens de transmissão em uma fila de transmissão e de entrega em uma fila de destino. Os gerenciadores de fila MSMQ implementam um protocolo de transferência de mensagens confiáveis para que as mensagens não serão perdidas durante a transmissão. O protocolo pode ser baseado em SOAP, como o SOAP mensagem protocolo SRMP (confiável) ou nativo.  
  
 No MSMQ, as filas podem ser transacional ou não transacional. Uma fila transacional permite que as mensagens ser capturada e entregues em uma transação e, em seguida, armazenadas de forma duradoura na fila. As mensagens enviadas para uma fila transacional são transferidas exatamente uma vez na ordem. Você pode usar uma fila não transacional para enviar mensagens duráveis e volátil. Uma mensagem enviada para uma fila não transacional não contém nenhuma garantia de transferência confiável; Portanto, as mensagens podem ser perdidas.  
  
 As filas do MSMQ também podem ser protegidas usando uma identidade de Windows registrada com o serviço de diretório do Active Directory. Ao instalar o MSMQ, você pode instalar a integração do Active Directory, o que exige que o computador é parte de uma rede de domínio do Windows.  
  
 Para obter mais informações sobre o MSMQ, consulte [instalar o enfileiramento de mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 O [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) é a associação enfileirada WCF fornece para os dois pontos de extremidade do WCF para se comunicar usando o MSMQ. A associação, portanto, expõe as propriedades que são específicas para o MSMQ. No entanto, nem todos os recursos do MSMQ e propriedades são expostas no `NetMsmqBinding`. O compact `NetMsmqBinding` foi projetado com um conjunto ideal de recursos de que a maioria dos clientes deve ser suficiente.  
  
 O `NetMsmqBinding` manifestos os principais conceitos de enfileiramento de mensagens discutidos até agora na forma de propriedades em associações. Essas propriedades, por sua vez, se comunicam com MSMQ como transferir e entregar as mensagens. Uma descrição das categorias de propriedade está nas seções a seguir. Para obter mais informações, consulte os tópicos conceituais que descrevem as propriedades específicas mais completamente.  
  
#### <a name="exactlyonce-and-durable-properties"></a>Propriedades duráveis e ExactlyOnce  
 O `ExactlyOnce` e `Durable` propriedades afetam como as mensagens são transferidas entre filas:  
  
-   `ExactlyOnce`: Quando definido como `true` (o padrão), o canal em fila garante que a mensagem, se fornecido, não sejam duplicada. Ele também garante que a mensagem não será perdida. Se a mensagem não pode ser entregue, ou a mensagem de tempo de vida expira antes que a mensagem pode ser entregue, junto com o motivo da falha de entrega a mensagem de falha é registrada em uma fila de mensagens mortas. Quando definido como `false`, o canal em fila torna um esforço para transferir a mensagem. Nesse caso, opcionalmente, você pode escolher uma fila de mensagens mortas.  
  
-   `Durable:` Quando definido como `true` (o padrão), o canal em fila garante que MSMQ armazena a mensagem de forma durável no disco. Assim, se o serviço MSMQ parar e reiniciar, as mensagens em disco é transferida para a fila de destino ou entregues ao serviço. Quando definido como `false`, as mensagens são armazenadas no repositório volátil e serão perdidas em interromper e reiniciar o serviço MSMQ.  
  
 Para `ExactlyOnce` transferência confiável, MSMQ requer a fila transacional. Além disso, o MSMQ exige uma transação ler de uma fila transacional. Dessa forma, quando você usa o `NetMsmqBinding`, lembre-se de que uma transação é necessária para enviar ou receber mensagens quando `ExactlyOnce` é definido como `true`. Da mesma forma, o MSMQ requer a fila não transacional por garantias de melhor esforço, como quando `ExactlyOnce` é `false` e para mensagens voláteis. Portanto, ao definir `ExactlyOnce` para `false` ou durável para `false`, não é possível enviar ou receber o uso de uma transação.  
  
> [!NOTE]
>  Certifique-se de que a fila correta (transacional ou não transacional) é criada com base nas configurações nas associações. Se `ExactlyOnce` é `true`, use uma fila transacional; caso contrário, use uma fila não transacional.  
  
#### <a name="dead-letter-queue-properties"></a>Propriedades da fila de mensagens mortas  
 A fila de mensagens mortas é usada para armazenar as mensagens com falha de entrega. O usuário pode gravar a lógica de compensação que lê mensagens fora da fila de mensagens mortas.  
  
 Fornecem muitos sistemas de enfileiramento de mensagens para uma fila de mensagens mortas de todo o sistema. MSMQ fornece uma fila de mensagens mortas não transacional todo o sistema para as mensagens com falha de entrega para filas não transacional e uma fila de mensagens mortas transacional todo o sistema de mensagens de falha de entrega para filas transacionais.  
  
 Se vários clientes enviando mensagens para filas de destino diferentes compartilharem o serviço do MSMQ, todas as mensagens enviadas pelos clientes vá para a mesma fila de mensagens mortas. Isso nem sempre é preferível. Para melhor isolamento, WCF e o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] fornecem uma fila de mensagens mortas personalizada (ou a fila de mensagens mortas específicas do aplicativo) que o usuário pode especificar para armazenar as mensagens com falha de entrega. Portanto, clientes diferentes não compartilham a mesma fila de mensagens mortas.  
  
 A associação tem duas propriedades de interesse:  
  
-   `DeadLetterQueue`: Esta propriedade é uma enumeração que indica se uma fila de mensagens mortas é solicitada. A enumeração também contém o tipo de fila de mensagens mortas, se for solicitado. Os valores são `None`, `System`, e `Custom`. Para obter mais informações sobre a interpretação dessas propriedades, consulte [usando filas de mensagens mortas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Essa propriedade é o endereço de identificador de recurso uniforme (URI) da fila de mensagens mortas específicas do aplicativo. Isso é necessário se `DeadLetterQueue`.`Custom` é escolhido.  
  
#### <a name="poison-message-handling-properties"></a>Propriedades de manipulação de mensagens suspeitas  
 Quando o serviço lê mensagens da fila de destino em uma transação, o serviço pode falhar ao processar a mensagem por vários motivos. A mensagem, em seguida, é colocada de volta para a fila a ser lido novamente. Para lidar com mensagens que falham repetidamente, um conjunto de tratamento de mensagens suspeitas de propriedades podem ser configuradas na associação. Há quatro propriedades: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, e `ReceiveErrorHandling`. Para obter mais informações sobre essas propriedades, consulte [manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Propriedades de segurança  
 MSMQ expõe seu próprio modelo de segurança, como listas de controle de acesso (ACLs) em uma fila ou enviar mensagens autenticadas. O `NetMsmqBinding` expõe essas propriedades de segurança como parte de suas configurações de segurança de transporte. Há duas propriedades na associação de segurança de transporte: `MsmqAuthenticationMode` e `MsmqProtectionLevel`. Configurações nessas propriedades dependem de como o MSMQ está configurado. Para obter mais informações, consulte [proteger mensagens usando a segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Além da segurança de transporte, a própria mensagem SOAP real pode ser protegida usando a segurança de mensagem. Para obter mais informações, consulte [proteger mensagens usando segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` também expõe duas propriedades, `MsmqEncryptionAlgorithm` e `MsmqHashAlgorithm`. Essas são as enumerações de algoritmos diferentes para escolher para criptografia de transferência de fila para a fila de mensagens e as assinaturas de hash.  
  
#### <a name="other-properties"></a>Outras propriedades  
 Além das propriedades acima, outras propriedades específicas do MSMQ expostas no incluem associação:  
  
-   `UseSourceJournal`: Uma propriedade para indicar que o diário de origem está ativada. Diário de origem é um recurso do MSMQ que mantém o controle de mensagens que foram transmitidas com êxito da fila de transmissão.  
  
-   `UseMsmqTracing`: Uma propriedade para indicar que o rastreamento do MSMQ está ativado. Rastreamento de MSMQ envia mensagens de relatório para uma fila de relatórios sempre que uma mensagem sai ou chega em um computador que hospeda um Gerenciador de fila MSMQ.  
  
-   `QueueTransferProtocol`: Uma enumeração do protocolo a ser usado para transferências de mensagem da fila para a fila. MSMQ implementa um protocolo de transferência de fila para a fila nativa e um protocolo baseado em SOAP, chamado de protocolo de mensagens confiável SOAP (SRMP). SRMP é usada ao usar o transporte HTTP para transferências de fila para a fila. SRMP segura é usada quando HTTPS é usado para transferências de fila para a fila.  
  
-   `UseActiveDirectory`: Um valor booleano para indicar se o Active Directory deve ser usado para resolução de endereço da fila. Por padrão, isso está desativado. Para obter mais informações, consulte [pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 O `MsmqIntegrationBinding` é usado quando um ponto de extremidade do WCF para se comunicar com um aplicativo existente do MSMQ escrito em C, C++, COM ou System.Messaging APIs.  
  
 As propriedades de associação são os mesmos para `NetMsmqBinding`. No entanto, as seguintes diferenças se aplicam:  
  
-   O contrato de operação para `MsmqIntegrationBinding` é restrito a fazer um único parâmetro do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> onde o parâmetro de tipo é o tipo de corpo.  
  
-   Muitas das propriedades de mensagem nativa do MSMQ são expostos no <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> para uso.  
  
-   Para ajudar com a serialização e desserialização do corpo da mensagem, serializadores como XML e ActiveX são fornecidos.  
  
### <a name="sample-code"></a>Código de exemplo  
 Para obter instruções passo a passo sobre como escrever WCF serviços que usam o MSMQ Consulte os tópicos a seguir:  
  
-   [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Para obter um exemplo de código completo que ilustra o uso do MSMQ no WCF, consulte os tópicos a seguir:  
  
-   [Associação transacionada do MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Comunicação em fila volátil](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Filas de mensagens mortas](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md)  
  
-   [Envio em lote transacionado](../../../../docs/framework/wcf/samples/transacted-batching.md)  
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Consulte também  
 [Pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [Hospedagem na Web de um aplicativo na fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
