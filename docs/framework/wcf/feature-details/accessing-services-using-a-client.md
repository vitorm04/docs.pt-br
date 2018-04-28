---
title: Usando um cliente para acessar um serviço
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2138a412af30812b4ff443963604dda52eafea11
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="accessing-services-using-a-client"></a>Usando um cliente para acessar um serviço
Aplicativos cliente devem criar, configurar e usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objetos de canal ou de cliente para se comunicar com os serviços. O [visão geral do cliente WCF](../../../../docs/framework/wcf/wcf-client-overview.md) tópico fornece uma visão geral de objetos e as etapas envolvidas na criação de objetos de cliente e o canal básico e usá-los.  
  
 Este tópico fornece informações detalhadas sobre alguns dos problemas com o cliente, aplicativos e objetos de cliente e o canal que podem ser úteis dependendo do cenário.  
  
## <a name="overview"></a>Visão geral  
 Este tópico descreve o comportamento e problemas relacionados a:  
  
-   Tempos de vida de canal e a sessão.  
  
-   Tratamento de exceções.  
  
-   Problemas de bloqueio de compreensão.  
  
-   Inicializando canais interativamente.  
  
### <a name="channel-and-session-lifetimes"></a>Canal e tempos de vida da sessão  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos inclui duas categorias de canais, datagrama e sessão.  
  
 Um *datagrama* canal é um canal no qual todas as mensagens são uncorrelated. Com um canal de datagrama, se uma operação de entrada ou saída falhar, a próxima operação é normalmente afetada e o mesmo canal pode ser reutilizado. Por isso, canais de datagrama normalmente não falhará.  
  
 *Sessão* canais, no entanto, são canais com uma conexão para outro ponto de extremidade. Mensagens em uma sessão em um lado sempre são correlacionadas com a mesma sessão do outro lado. Além disso, ambos os participantes em uma sessão devem concordar que os requisitos de sua conversa foram atendidos para a sessão seja considerada bem-sucedida. Se não puderem concordar, o canal de sessão pode falhar.  
  
 Abra os clientes implicitamente ou explicitamente chamando a primeira operação.  
  
> [!NOTE]
>  Tentativa de detectar explicitamente os canais de sessão com falha não é normalmente útil, porque quando você é notificado variam de acordo com a implementação de sessão. Por exemplo, porque o <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (com a sessão confiável desabilitada) revela a sessão de conexão TCP, se você ouvir o <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> evento sobre o serviço ou o cliente provavelmente ser notificado rapidamente no caso de falha de rede. Sessões confiáveis (estabelecida por associações no qual o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> estiver habilitado) são projetados para isolar serviços de falhas de rede pequena. Se a sessão pode ser restabelecida dentro de um período de tempo, a mesma associação — configurado para sessões confiáveis — talvez não falhará até que a interrupção de continuação para um período de tempo maior.  
  
 A maioria das associações fornecidas pelo sistema (que expõem os canais para a camada de aplicativo) usa sessões por padrão, mas o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> não. Para obter mais informações, consulte [sessões usando](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>O uso adequado de sessões  
 Sessões fornecem uma maneira de saber se a troca de mensagem inteira é concluída, e se ambos os lados consideraram bem-sucedido. É recomendável que um aplicativo de chamada abrir o canal, usá-lo e feche o canal de dentro do bloco try de uma. Se um canal de sessão estiver aberto e o <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> método é chamado uma vez e essa chamada retorna com êxito, a sessão foi bem-sucedida. Bem-sucedida nesse caso significa que todas as entregas garante a associação especificada foi atendida e o outro lado não chamou <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> no canal antes de chamar <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 A seção a seguir fornece um exemplo dessa abordagem de cliente.  
  
### <a name="handling-exceptions"></a>Tratando exceções  
 Tratamento de exceções em aplicativos cliente é simples. Se um canal é aberto, usado e fechado dentro de um bloco try, em seguida, a conversa foi bem-sucedida, a menos que uma exceção será lançada. Normalmente, se uma exceção será lançada a conversa será anulada.  
  
> [!NOTE]
>  Usar o `using` instrução (`Using` no Visual Basic) não é recomendado. Isso ocorre porque o fim do `using` instrução pode causar exceções que podem mascarar outras exceções, você precisará conhecer. Para obter mais informações, consulte [evitando problemas com a instrução Using](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 O exemplo de código a seguir mostra o padrão de cliente recomendada usando um bloco try/catch e não o `using` instrução.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Verificando o valor de <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> propriedade é uma condição de corrida e não é recomendada para determinar se deseja reutilizar ou fechar um canal.  
  
 Canais de datagrama nunca falha mesmo se as exceções ocorrem quando eles forem fechados. Além disso, os clientes não-duplex que falham ao autenticar usando uma conversa segura normalmente geram um <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. No entanto se o cliente duplex usando uma conversa segura não for autenticado, o cliente recebe um <xref:System.TimeoutException?displayProperty=nameWithType> em vez disso.  
  
 Para obter informações mais completas sobre como trabalhar com as informações de erro no nível do aplicativo, consulte [especificando e tratamento de falhas em contratos e serviços](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) descreve exceções esperadas e mostra como lidar com eles. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] como manipular erros durante o desenvolvimento de canais, consulte [tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Bloqueio de cliente e o desempenho  
 Quando um aplicativo chama sincronicamente uma operação de solicitação-resposta, os blocos de cliente até que um valor de retorno é recebido ou uma exceção (como uma <xref:System.TimeoutException?displayProperty=nameWithType>) é gerada. Esse comportamento é semelhante ao comportamento de local. Quando um aplicativo de forma síncrona chama uma operação em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objeto do cliente ou canal, o cliente não retorna até que a camada do canal pode gravar os dados na rede ou até que uma exceção será lançada. E ao padrão de troca de mensagem unidirecional (especificado marcando uma operação com <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> definida como `true`) pode fazer alguns clientes também podem bloquear operações unidirecionais e mais ágil na resposta, dependendo da associação e quais mensagens já foram enviado. Operações unidirecionais são apenas sobre a troca de mensagens, não mais, nem menos. Para obter mais informações, consulte [unidirecional serviços](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Blocos de dados grandes podem reduzir a velocidade de processamento não importa qual o padrão de troca de mensagens de cliente. Para entender como lidar com esses problemas, consulte [dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Se seu aplicativo deve fazer mais trabalho, enquanto uma operação é concluída, você deve criar um par de métodos assíncronos na interface de contrato de serviço que sua [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente implementa. A maneira mais fácil de fazer isso é usar o `/async` alternar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Para obter um exemplo, consulte [como: chamar operações de serviço assíncrona](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] aumentando o desempenho do cliente, consulte [aplicativos de cliente de camada intermediária](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Permitir que o usuário selecionar credenciais dinamicamente  
 O <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> interface permite que os aplicativos exibir uma interface de usuário que permite que o usuário escolha credenciais com o qual um canal é criado antes de iniciar os timers de tempo limite.  
  
 Os desenvolvedores de aplicativos podem fazer uso de um inserido <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> de duas maneiras. O aplicativo cliente pode chamar tanto <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ou uma versão assíncrona) antes de abrir o canal (o *explícita* abordagem) ou ligue para a primeira operação (o *implícita*abordagem).  
  
 Se usar a abordagem implícita, o aplicativo deve chamar a primeira operação em um <xref:System.ServiceModel.ClientBase%601> ou <xref:System.ServiceModel.IClientChannel> extensão. Se ele chama qualquer coisa que não seja a primeira operação, uma exceção será lançada.  
  
 Se usar a abordagem explícita, o aplicativo deve executar as seguintes etapas na ordem:  
  
1.  Chame <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ou uma versão assíncrona).  
  
2.  Quando os inicializadores tem retornado, chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método no <xref:System.ServiceModel.IClientChannel> objeto ou no <xref:System.ServiceModel.IClientChannel> objeto retornado do <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> propriedade.  
  
3.  Chamar as operações.  
  
 É recomendável que os aplicativos de qualidade de produção controlam o processo de interface do usuário adotando a abordagem explícita.  
  
 Aplicativos que usam a abordagem implícita invocar os inicializadores de interface do usuário, mas se o usuário do aplicativo não responder dentro do período de tempo limite de envio da associação, uma exceção é lançada quando a interface do usuário retorna.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)  
 [Como acessar os serviços com contratos unidirecionais e de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Como acessar serviços com um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Como acessar um WSE 3.0 Service](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Como usar o ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)  
 [Como chamar operações de serviço de forma assíncrona](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Aplicativos cliente de camada intermediária](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
