---
title: Enfileiramento no WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: f04055df2c6d4b0a51b36040a5b377bb8738c534
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086590"
---
# <a name="queuing-in-wcf"></a>Enfileiramento no WCF
Esta seção descreve como usar a comunicação em fila no Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Associação de transporte de filas como um WCF  
 No WCF, os contratos de especificam o que está sendo trocado. Os contratos são trocas de mensagens de aplicativo específico ou dependentes de negócios. O mecanismo usado para trocar mensagens (ou "como") é especificado nas associações. Associações do WCF encapsulam detalhes de troca de mensagens. Elas expõem os botões de configuração para o usuário controlar vários aspectos de transporte ou protocolo que representam as associações. Enfileiramento no WCF é tratado como qualquer outra associação de transporte, que é uma grande vantagem para muitos aplicativos de enfileiramento de mensagens. Hoje, muitos aplicativos de enfileiramento de mensagens são escritos de maneiras diferentes de outra chamada de procedimento remoto (RPC)-estilo de aplicativos distribuídos, tornando mais difícil de seguir e manter. Com o WCF, o estilo de escrever um aplicativo distribuído é muito semelhante a, tornando mais fácil de seguir e manter. Além disso, ao fatorar o mecanismo de troca separadamente da lógica de negócios, é mais fácil de configurar o transporte ou fazer alterações sem afetar o código específico do aplicativo. A figura a seguir ilustra a estrutura de um serviço WCF e o cliente usando o MSMQ como transporte.  
  
 ![Na fila de diagrama de aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Como você pode ver na figura anterior, o cliente e o serviço devem definir apenas a semântica de aplicativo, ou seja, o contrato e a implementação. O serviço define uma associação enfileirada com configurações preferenciais. O cliente usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um cliente WCF para o serviço e para gerar um arquivo de configuração que descreve as associações de usar para enviar mensagens para o serviço. Portanto, para enviar uma mensagem na fila, o cliente cria uma instância de um cliente WCF e invoca uma operação nele. Isso faz com que a mensagem ser enviada à fila de transmissão e transferidos para a fila de destino. Todas as complexidades de comunicação em fila estão ocultos do aplicativo que está enviando e recebendo mensagens.  
  
 Advertências sobre a associação enfileirada no WCF incluem:  
  
-   Serviço todas as operações devem ser unidirecionais, porque o padrão na fila de associação no WCF não oferece suporte para o uso de filas de comunicação duplex. Um exemplo de comunicação bidirecional ([comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md)) ilustra como usar dois contratos unidirecionais para implementar o uso de filas de comunicação duplex.  
  
-   Para gerar um WCF usando a troca de metadados do cliente requer um ponto de extremidade HTTP adicional no serviço de modo que possam ser consultado diretamente para gerar o cliente do WCF e obter informações de associação para configurar adequadamente a comunicação em fila.  
  
-   Configuração adicional fora do WCF com base na associação em fila, é necessária. Por exemplo, o <xref:System.ServiceModel.NetMsmqBinding> classe que é fornecido com o WCF exige que você configure as ligações, bem como a configurar minimamente Message Queuing (MSMQ).  
  
 As seções a seguir descrevem as específicas na fila associações fornecidas com o WCF, que se baseiam em MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 O transporte em fila no WCF usa MSMQ para a sua comunicação em fila.  
  
 MSMQ é fornecido como um componente opcional do Windows e é executado como um serviço NT. Ele captura as mensagens para transmissão em uma fila de transmissão e para entrega em uma fila de destino. Os gerenciadores de fila do MSMQ implementam um protocolo de transferência de mensagens confiável, de modo que as mensagens não são perdidas durante a transmissão. O protocolo pode ser nativo ou baseado em SOAP, como o Reliable mensagem de protocolo SRMP (SOAP).  
  
 No MSMQ, filas podem ser transacional ou não transacional. Uma fila transacional permite ser capturados e entregues em uma transação e, em seguida, armazenadas de forma duradoura na fila de mensagens. As mensagens enviadas para uma fila transacional são transferidas exatamente uma vez na ordem. Você pode usar uma fila não transacional para enviar mensagens voláteis e duráveis. Uma mensagem enviada para uma fila não transacional não contém quaisquer garantias de transferência confiável; Portanto, as mensagens podem ser perdidas.  
  
 Filas MSMQ também podem ser protegidas usando uma identidade de Windows registrada com o serviço de diretório do Active Directory. Ao instalar o MSMQ, você pode instalar a integração do Active Directory, o que exige que o computador é parte de uma rede de domínio do Windows.  
  
 Para obter mais informações sobre o MSMQ, consulte [instalar o enfileiramento de mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 O [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) é a associação em fila, o WCF fornece para os dois pontos de extremidade do WCF para se comunicar usando o MSMQ. A associação, portanto, expõe propriedades que são específicas para o MSMQ. No entanto, nem todos os recursos do MSMQ e as propriedades são expostas no `NetMsmqBinding`. O compact `NetMsmqBinding` destina-se com um conjunto ideal de recursos de que a maioria dos clientes deve ser suficiente.  
  
 O `NetMsmqBinding` manifestos de enfileiramento de mensagens conceitos discutidos até o momento na forma de propriedades em associações. Essas propriedades, por sua vez, comunicar-se para o MSMQ como transferir e entregar as mensagens. Uma discussão sobre as categorias de propriedade está nas seções a seguir. Para obter mais informações, consulte os tópicos conceituais que descrevem as propriedades específicas mais completamente.  
  
#### <a name="exactlyonce-and-durable-properties"></a>Propriedades duráveis e ExactlyOnce  
 O `ExactlyOnce` e `Durable` propriedades afetam a forma como as mensagens são transferidas entre filas:  
  
-   `ExactlyOnce`: Quando definido como `true` garante que o canal em fila (padrão), que a mensagem, se fornecido, não é duplicada. Ela também garante que a mensagem não será perdida. Se a mensagem não pode ser entregue ou a mensagem de tempo para Live expira antes que a mensagem pode ser entregue, a mensagem com falha, juntamente com o motivo da falha de entrega é registrada em uma fila de inatividade. Quando definido como `false`, o canal em fila torna um esforço para transferir a mensagem. Nesse caso, você pode escolher, opcionalmente, uma fila de inatividade.  
  
-   `Durable:` Quando definido como `true` garante que o canal em fila (padrão), que MSMQ armazena a mensagem de forma permanente em disco. Portanto, se o serviço MSMQ parar e reiniciar, as mensagens em disco é transferida para a fila de destino ou entregues ao serviço. Quando definido como `false`, as mensagens são armazenadas no repositório volátil e serão perdidas em interromper e reiniciar o serviço MSMQ.  
  
 Para `ExactlyOnce` transferência confiável, a fila seja transacional requer do MSMQ. Além disso, o MSMQ exige uma transação leia de uma fila transacional. Dessa forma, quando você usa o `NetMsmqBinding`, lembre-se de que uma transação é necessário para enviar ou receber mensagens quando `ExactlyOnce` é definido como `true`. Da mesma forma, o MSMQ requer a fila não transacional de garantias de melhor esforço, por exemplo, quando `ExactlyOnce` é `false` e para mensagens voláteis. Portanto, ao definir `ExactlyOnce` para `false` ou duráveis para `false`, não é possível enviar ou receber o uso de uma transação.  
  
> [!NOTE]
>  Certifique-se de que a fila correta (transacional ou não transacional) é criada com base nas configurações nas associações. Se `ExactlyOnce` é `true`, use uma fila transacional; caso contrário, use uma fila não transacional.  
  
#### <a name="dead-letter-queue-properties"></a>Propriedades da fila de inatividade  
 A fila de inatividade é usada para armazenar mensagens que falham na entrega. O usuário pode gravar a lógica de compensação que lê mensagens fora da fila de inatividade.  
  
 Fornecem muitos sistemas de enfileiramento de mensagens para uma fila de inatividade em todo o sistema. MSMQ fornece uma fila de inatividade não-transacional em todo o sistema para mensagens que falham na entrega para filas não transacionais e de uma fila de inatividade transacional em todo o sistema de mensagens que falham na entrega para filas transacionais.  
  
 Se vários clientes enviando mensagens para filas de destino diferentes compartilharem o serviço MSMQ, todas as mensagens enviadas pelos clientes vá para a mesma fila de inatividade. Isso nem sempre é preferível. Para melhor isolamento, WCF e o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)] fornecem uma fila de mensagens mortas personalizada (ou a fila de inatividade específico do aplicativo) que o usuário pode especificar para armazenar mensagens que falham na entrega. Portanto, clientes diferentes não compartilham a mesma fila de inatividade.  
  
 A associação tem duas propriedades de interesse:  
  
-   `DeadLetterQueue`: Esta propriedade é uma enumeração que indica se a uma fila de inatividade é solicitada. A enumeração também contém o tipo de fila de inatividade, se ela for solicitada. Os valores são `None`, `System`, e `Custom`. Para obter mais informações sobre a interpretação dessas propriedades, consulte [usando filas para lidar com falhas de transferência de mensagem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Essa propriedade é o endereço de identificador de recurso uniforme (URI) da fila de inatividade específico do aplicativo. Isso é necessário se `DeadLetterQueue`.`Custom` é escolhido.  
  
#### <a name="poison-message-handling-properties"></a>Propriedades de manipulação de mensagens suspeitas  
 Quando o serviço lê as mensagens da fila de destino em uma transação, o serviço pode falhar ao processar a mensagem por vários motivos. A mensagem, em seguida, é colocada de volta na fila a ser lido novamente. Para lidar com mensagens que falham repetidamente, um conjunto de manipulação de mensagens suspeitas propriedades podem ser configuradas na associação. Há quatro propriedades: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, e `ReceiveErrorHandling`. Para obter mais informações sobre essas propriedades, consulte [manipulação de mensagens suspeitas](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Propriedades de segurança  
 MSMQ expõe seu próprio modelo de segurança, como listas de controle de acesso (ACLs) em uma fila ou enviar mensagens autenticadas. O `NetMsmqBinding` expõe essas propriedades de segurança como parte de suas configurações de segurança de transporte. Há duas propriedades na associação para a segurança de transporte: `MsmqAuthenticationMode` e `MsmqProtectionLevel`. As configurações nessas propriedades dependem de como o MSMQ está configurado. Para obter mais informações, consulte [Protegendo mensagens usando segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Além da segurança de transporte, a mensagem SOAP real em si pode ser protegida usando a segurança de mensagem. Para obter mais informações, consulte [Protegendo mensagens usando segurança de mensagem](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` também expõe duas propriedades, `MsmqEncryptionAlgorithm` e `MsmqHashAlgorithm`. Essas são as enumerações de algoritmos diferentes para escolher para as assinaturas de hash e criptografia de fila para a fila de transferência de mensagens.  
  
#### <a name="other-properties"></a>Outras propriedades  
 Além das propriedades anteriores, outras propriedades específicas de MSMQ expostas de inclusão de associação:  
  
-   `UseSourceJournal`: Uma propriedade para indicar que o diário de origem é ativada. Diário de origem é um recurso MSMQ que mantém o controle de mensagens que foram transmitidas com êxito da fila de transmissão.  
  
-   `UseMsmqTracing`: Uma propriedade para indicar que o rastreamento do MSMQ está ativado. Rastreamento de MSMQ envia mensagens de relatório para uma fila de relatórios sempre que uma mensagem sai ou chega a um computador que hospeda um Gerenciador de fila do MSMQ.  
  
-   `QueueTransferProtocol`: Uma enumeração do protocolo a ser usado para transferências de mensagens da fila para a fila. MSMQ implementa um protocolo de transferência de fila para a fila nativo e um protocolo baseado em SOAP chamado Reliable Messaging protocolo SRMP (SOAP). SRMP é usado ao usar o transporte HTTP para transferências de fila para a fila. SRMP segura é usada quando HTTPS é usado para transferências de fila para a fila.  
  
-   `UseActiveDirectory`: Um valor booliano para indicar se o Active Directory deve ser usado para resolução de endereço da fila. Por padrão, isso está desativado. Para obter mais informações, consulte [pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 O `MsmqIntegrationBinding` é usado quando você deseja um ponto de extremidade do WCF para se comunicar com um aplicativo de MSMQ existente, escrito em C, C++, COM ou System.Messaging APIs.  
  
 As propriedades de associação são os mesmos para `NetMsmqBinding`. No entanto, as seguintes diferenças se aplicam:  
  
-   O contrato de operação para `MsmqIntegrationBinding` restrita para colocar um único parâmetro do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> onde o parâmetro de tipo é o tipo de corpo.  
  
-   Grande parte das propriedades de mensagem nativa do MSMQ são expostos no <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> para uso.  
  
-   Para ajudar com a serialização e desserialização do corpo da mensagem, os serializadores como XML e ActiveX são fornecidos.  
  
### <a name="sample-code"></a>Código de exemplo  
 Para obter instruções passo a passo sobre como escrever o WCF, serviços que usam o MSMQ Consulte os tópicos a seguir:  
  
-   [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Como trocar mensagens na fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Para obter um exemplo de código completo ilustrando o uso do MSMQ no WCF, consulte os tópicos a seguir:  
  
-   [Associação transacionada do MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Comunicação em fila volátil](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Filas de mensagens mortas](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Consulte também  
 [Pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [Hospedagem na Web de um aplicativo na fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
