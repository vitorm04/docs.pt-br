---
title: Enfileiramento no WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: e6608a3d556b546660be904eb8c853243e833d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184556"
---
# <a name="queuing-in-wcf"></a>Enfileiramento no WCF
Esta seção descreve como usar a comunicação enfileirada na Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Filas como uma vinculação de transporte WCF  
 No WCF, os contratos especificam o que está sendo trocado. Os contratos são trocas de mensagens dependentes de negócios ou específicas de aplicativos. O mecanismo usado para trocar mensagens (ou o "como") é especificado nas vinculações. As vinculações no WCF encapsulam detalhes da troca de mensagens. Eles expõem os botões de configuração para o usuário controlar vários aspectos do transporte ou do protocolo que as vinculações representam. A fila no WCF é tratada como qualquer outra vinculação de transporte, o que é uma grande vantagem para muitos aplicativos de fila. Hoje, muitos aplicativos de fila são escritos de forma diferente de outros aplicativos distribuídos no estilo RPC (Remote Procedure Call, chamada de procedimento remoto), tornando mais difícil de seguir e manter. Com o WCF, o estilo de escrever um aplicativo distribuído é muito o mesmo, facilitando o seguimento e a manutenção. Além disso, ao fatorar o mecanismo de troca separadamente da lógica empresarial, é mais fácil configurar o transporte ou fazer alterações nele sem afetar o código específico do aplicativo. A figura a seguir ilustra a estrutura de um serviço wcf e cliente usando MSMQ como transporte.  
  
 ![Diagrama de aplicativos enfileirados](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura de fila distribuída")  
  
 Como você pode ver na figura anterior, o cliente e o serviço devem definir apenas a semântica do aplicativo, ou seja, o contrato e a implementação. O serviço configura uma vinculação enfileirada com configurações preferenciais. O cliente usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar um cliente WCF para o serviço e para gerar um arquivo de configuração que descreve as vinculações a serem usados para enviar mensagens ao serviço. Assim, para enviar uma mensagem enfileirada, o cliente instancia um cliente WCF e invoca uma operação nele. Isso faz com que a mensagem seja enviada para a fila de transmissão e transferida para a fila de destino. Todas as complexidades da comunicação enfileirada estão ocultas do aplicativo que está enviando e recebendo mensagens.  
  
 As ressalvas sobre a vinculação enfileirada no WCF incluem:  
  
- Todas as operações de serviço devem ser unidirecionais porque a vinculação enfileirada padrão no WCF não suporta comunicação duplex usando filas. Uma amostra de comunicação bidirecional[(Comunicação Bidirecional)](../../../../docs/framework/wcf/samples/two-way-communication.md)ilustra como usar dois contratos unidirecionais para implementar a comunicação duplex usando filas.  
  
- Para gerar um cliente WCF usando a troca de metadados requer um ponto final HTTP adicional no serviço para que ele possa ser consultado diretamente para gerar o cliente WCF e obter informações vinculativas para configurar adequadamente a comunicação enfileirada.  
  
- Com base na vinculação enfileirada, é necessária uma configuração extra fora do WCF. Por exemplo, <xref:System.ServiceModel.NetMsmqBinding> a classe enviada com OWCF exige que você configure as vinculações, bem como configure minimamente a fila de mensagens (MSMQ).  
  
 As seções a seguir descrevem as vinculações específicas enfileiradas enviadas com WCF, que são baseadas no MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 O transporte enfileirado no WCF usa o MSMQ para sua comunicação enfileirada.  
  
 O MSMQ é fornecido como um componente opcional com windows e funciona como um serviço NT. Ele captura mensagens para transmissão em uma fila de transmissão e para entrega em uma fila de destino. Os gerentes de fila do MSMQ implementam um protocolo confiável de transferência de mensagens para que as mensagens não sejam perdidas na transmissão. O protocolo pode ser nativo ou baseado em SOAP, como o SOAP Reliable Message Protocol (SRMP).  
  
 No MSMQ, as filas podem ser transacionais ou não transacionais. Uma fila transacional permite que as mensagens sejam capturadas e entregues em uma transação e, em seguida, armazenadas duramente na fila. As mensagens enviadas para uma fila transacional são transferidas exatamente uma vez em ordem. Você pode usar uma fila não transacional para enviar mensagens voláteis e duráveis. Uma mensagem enviada para uma fila não transacional não possui garantias de transferência confiáveis; assim, as mensagens podem ser perdidas.  
  
 As filas mSMQ também podem ser protegidas usando uma identidade do Windows registrada no serviço de diretório do Active Directory. Ao instalar o MSMQ, você pode instalar a integração do Active Directory, que exige que o computador faça parte de uma rede de domínio do Windows.  
  
 Para obter mais informações sobre o MSMQ, consulte [Instalação de fila de mensagens (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 O [ \<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) é o WCF de vinculação enfileirado que fornece dois pontos finais do WCF para se comunicar usando o MSMQ. A vinculação, portanto, expõe propriedades específicas do MSMQ. No entanto, nem todas as características e `NetMsmqBinding`propriedades do MSMQ estão expostas no . O `NetMsmqBinding` compacto é projetado com um conjunto ideal de recursos que a maioria dos clientes deve encontrar suficiente.  
  
 O `NetMsmqBinding` manifesto dos conceitos centrais de fila discutidos até agora na forma de propriedades nas vinculações. Essas propriedades, por sua vez, comunicam ao MSMQ como transferir e entregar as mensagens. A discussão das categorias de propriedade está nas seguintes seções. Para obter mais informações, consulte os tópicos conceituais que descrevem as propriedades específicas de forma mais completa.  
  
#### <a name="exactlyonce-and-durable-properties"></a>Exatamenteonce e Propriedades Duráveis  
 As `ExactlyOnce` `Durable` propriedades e afetam a forma como as mensagens são transferidas entre filas:  
  
- `ExactlyOnce`: Quando `true` definido como (o padrão), o canal enfileirado garante que a mensagem, se entregue, não seja duplicada. Também garante que a mensagem não seja perdida. Se a mensagem não puder ser entregue ou a mensagem Time-To Live expirar antes que a mensagem possa ser entregue, a mensagem falhada, juntamente com a razão da falha de entrega, será gravada em uma fila de letras mortas. Quando configurado para `false`, o canal enfileirado faz um esforço para transferir a mensagem. Neste caso, você pode escolher opcionalmente uma fila de letras mortas.  
  
- `Durable:`Quando definido `true` como (o padrão), o canal enfileirado garante que o MSMQ armate a mensagem duramente no disco. Assim, se o serviço MSMQ parar e reiniciar, as mensagens no disco serão transferidas para a fila de destino ou entregues ao serviço. Quando `false`configuradas, as mensagens são armazenadas em armazenamento volátil e são perdidas ao parar e reiniciar o serviço MSMQ.  
  
 Para `ExactlyOnce` uma transferência confiável, o MSMQ requer que a fila seja transacional. Além disso, o MSMQ requer uma transação para ler a partir de uma fila transacional. Como tal, ao `NetMsmqBinding`usar o , lembre-se de que `ExactlyOnce` uma transação é necessária para enviar ou receber mensagens quando estiver definida para `true`. Da mesma forma, o MSMQ exige que a fila não seja transacional para garantias de melhor esforço, como quando `ExactlyOnce` é `false` e para mensagens voláteis. Assim, ao `ExactlyOnce` `false` definir ou `false`durável para , você não pode enviar ou receber usando uma transação.  
  
> [!NOTE]
> Certifique-se de que a fila correta (transacional ou não transacional) seja criada com base nas configurações nas vinculações. Se `ExactlyOnce` `true`for, use uma fila transacional; caso contrário, use uma fila não transacional.  
  
#### <a name="dead-letter-queue-properties"></a>Propriedades da fila de letras mortas  
 A fila de letras mortas é usada para armazenar mensagens que falham na entrega. O usuário pode escrever uma lógica de compensação que lê mensagens fora da fila de letras mortas.  
  
 Muitos sistemas de fila fornecem uma fila de letras mortas em todo o sistema. O MSMQ fornece uma fila de letras mortas não transacionais em todo o sistema para mensagens que falham na entrega de filas não transacionais e uma fila de letras mortas transacionais em todo o sistema para mensagens que falham na entrega de filas transacionais.  
  
 Se vários clientes que enviam mensagens para diferentes filas de destino compartilharem o serviço MSMQ, todas as mensagens enviadas pelos clientes vão para a mesma fila de letras mortas. Isso nem sempre é preferível. Para um melhor isolamento, o WCF e o MSMQ no Windows Vista fornecem uma fila de letras mortas personalizada (ou fila de letra morta específica do aplicativo) que o usuário pode especificar para armazenar mensagens que falham na entrega. Portanto, clientes diferentes não compartilham a mesma fila de letras mortas.  
  
 A vinculação tem duas propriedades de interesse:  
  
- `DeadLetterQueue`: Esta propriedade é uma enumeração que indica se uma fila de letras mortas é solicitada. A enumeração também contém o tipo de fila de letras mortas, se uma for solicitada. Os valores são `None`, `System` e `Custom`. Para obter mais informações sobre a interpretação dessas propriedades, consulte [Usando filas de letras mortas para lidar com falhas de transferência de mensagens](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Esta propriedade é o endereço URI (Uniform Resource Identifier, identificador de recursos uniformes) da fila de letras mortas específica do aplicativo. Isso é `DeadLetterQueue`necessário se .`Custom` é escolhido.  
  
#### <a name="poison-message-handling-properties"></a>Propriedades de manuseio de mensagens venenosas  
 Quando o serviço lê mensagens da fila de destino em uma transação, o serviço pode não processar a mensagem por várias razões. A mensagem é então colocada de volta na fila para ser lida novamente. Para lidar com mensagens que falham repetidamente, um conjunto de propriedades de manuseio de mensagens venenosas pode ser configurado na vinculação. Existem quatro `ReceiveRetryCount`propriedades: `RetryCycleDelay`, `ReceiveErrorHandling` `MaxRetryCycles`e . Para obter mais informações sobre essas propriedades, consulte [Poison Message Handling](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Propriedades de segurança  
 O MSMQ expõe seu próprio modelo de segurança, como listas de controle de acesso (ACLs) em uma fila ou envio de mensagens autenticadas. O `NetMsmqBinding` expõe essas propriedades de segurança como parte de suas configurações de segurança de transporte. Existem duas propriedades na vinculação `MsmqAuthenticationMode` `MsmqProtectionLevel`para segurança de transporte: e . As configurações nessas propriedades dependem de como o MSMQ está configurado. Para obter mais informações, consulte [Protegendo mensagens usando a segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Além da segurança de transporte, a própria mensagem SOAP real pode ser protegida usando a segurança da mensagem. Para obter mais informações, consulte [Proteger mensagens usando a segurança de mensagens](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity`também expõe duas `MsmqEncryptionAlgorithm` propriedades, e `MsmqHashAlgorithm`. Estas são enumerações de diferentes algoritmos para escolher para a criptografia de transferência de fila para fila de mensagens e hashing das assinaturas.  
  
#### <a name="other-properties"></a>Outras propriedades  
 Além das propriedades anteriores, outras propriedades específicas do MSMQ expostas na vinculação incluem:  
  
- `UseSourceJournal`: Uma propriedade para indicar que o diário de origem está ligado. O diário de origem é um recurso MSMQ que mantém o controle das mensagens que foram transmitidas com sucesso da fila de transmissão.  
  
- `UseMsmqTracing`: Uma propriedade para indicar que o rastreamento MSMQ está ligado. O rastreamento do MSMQ envia mensagens de relatório para uma fila de relatórios cada vez que uma mensagem sai ou chega a uma máquina hospedando um gerenciador de fila smq.  
  
- `QueueTransferProtocol`: Uma enumeração do protocolo a ser usado para transferências de mensagens de fila para fila. O MSMQ implementa um protocolo nativo de transferência de fila para fila e um protocolo baseado em SOAP chamado SOAP Reliable Messaging Protocol (SRMP). O SRMP é usado ao usar o transporte HTTP para transferências de fila para fila. O seguro SRMP é usado ao usar HTTPS para transferências de fila para fila.  
  
- `UseActiveDirectory`: Um valor booleano para indicar se o Diretório Ativo deve ser usado para resolução de endereços de fila. Por padrão, isso está desligado. Para obter mais informações, consulte [Pontos finais de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 O `MsmqIntegrationBinding` é usado quando você deseja que um ponto final do WCF se comunique com um aplicativo MSMQ existente escrito em C, C++, COM ou APIs do System.Messaging.  
  
 As propriedades de ligação `NetMsmqBinding`são as mesmas para . No entanto, as seguintes diferenças se aplicam:  
  
- O contrato `MsmqIntegrationBinding` de operação é restrito a <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> tomar um único parâmetro do tipo onde o parâmetro tipo é o tipo de corpo.  
  
- Grande parte das propriedades de mensagem nativa <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> do MSMQ são expostas no para uso.  
  
- Para ajudar na serialização e desserialização do corpo da mensagem, serializadores como XML e ActiveX são fornecidos.  
  
### <a name="sample-code"></a>Exemplo de código  
 Para obter instruções passo a passo sobre como escrever serviços WCF que usam mSMQ, consulte os seguintes tópicos:  
  
- [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Como fazer intercâmbio de mensagens em fila com pontos de extremidade do WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Para obter uma amostra de código concluída ilustrando o uso do MSMQ no WCF, consulte os seguintes tópicos:  
  
- [Associação transacionada do MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Comunicação em fila volátil](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Filas de mensagens de inatividade](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Sessões e filas](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md)
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Confira também

- [Pontos de extremidade de serviço e endereçamento de fila](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Hospedagem na Web de um aplicativo na fila](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
