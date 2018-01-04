---
title: "Utilizando sessões"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b7691b1c105ceb3e209c5d86bda455657a4198
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-sessions"></a>Utilizando sessões
Em [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos, um *sessão* correlaciona a um grupo de mensagens em uma conversa. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]as sessões são diferentes do objeto de sessão disponível no [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplicativos, suporte a comportamentos diferentes e são controlados de maneiras diferentes. Este tópico descreve os recursos que permitem que as sessões no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos e como usá-los.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sessões em aplicativos do Windows Communication Foundation  
 Quando um contrato de serviço Especifica que ele requer uma sessão, esse contrato é Especifica que todas as chamadas (ou seja, as subjacente trocas de mensagens que oferecem suporte as chamadas) devem ser parte da mesma conversa. Se um contrato especifica que permite que as sessões, mas não requer um, os clientes podem se conectar e a estabelecer uma sessão ou não estabelecer uma sessão. Se a sessão é encerrada e uma mensagem é enviada por meio do canal mesmo que uma exceção será lançada.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]as sessões têm os seguintes recursos conceituais principais:  
  
-   Eles são explicitamente iniciados e finalizados pelo aplicativo de chamada (o cliente do WCF).  
  
-   Mensagens entregues durante uma sessão são processadas na ordem em que são recebidos.  
  
-   Sessões de correlação um grupo de mensagens em uma conversa. Tipos diferentes de correlação são possíveis. Por exemplo, um canal de sessão pode correlacionar as mensagens com base em uma conexão de rede compartilhada enquanto outro canal baseadas em sessão pode correlacionar as mensagens com base em uma marca compartilhada no corpo da mensagem. Os recursos que podem ser derivados da sessão dependem da natureza da correlação.  
  
-   Há um repositório de dados gerais associado com um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sessão.  
  
 Se você estiver familiarizado com o <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> classe em [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplicativos e a funcionalidade que ela fornece, você observará as seguintes diferenças entre esse tipo de sessão e [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sessões:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]as sessões são sempre iniciadas pelo servidor.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]as sessões são implicitamente não ordenadas.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]sessões fornecem um mecanismo de armazenamento de dados gerais em solicitações.  
  
 Este tópico descreve:  
  
-   O comportamento de execução padrão ao usar associações baseadas em sessão na camada de modelo de serviço.  
  
-   Os tipos de recursos que o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornecem associações baseadas em sessão, fornecido pelo sistema.  
  
-   Como criar um contrato que declara um requisito de sessão.  
  
-   Como entender e controlar a criação e o encerramento da sessão e a relação da sessão para a instância do serviço.  
  
## <a name="default-execution-behavior-using-sessions"></a>Usando sessões de comportamento de execução padrão  
 Uma associação que tenta iniciar uma sessão é chamada um *baseadas em sessão* associação. Contratos de serviço especificar que eles exigem, permitirem ou recusam associações baseadas em sessão, definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade na interface de contrato de serviço (ou classe) para um do <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> valores de enumeração. Por padrão, o valor dessa propriedade é <xref:System.ServiceModel.SessionMode.Allowed>, que significa que, se um cliente usa uma associação com base em sessão com um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implementação de serviço, o serviço estabelece e usa a sessão fornecida.  
  
 Quando um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço aceita uma sessão de cliente, os seguintes recursos são habilitados por padrão:  
  
1.  Todas as chamadas entre um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto de cliente são tratadas pela mesma instância de serviço.  
  
2.  Ligações diferentes com base em sessão fornecem funcionalidades adicionais.  
  
## <a name="system-provided-session-types"></a>Tipos de sessão fornecido pelo sistema  
 Uma associação baseada em sessão oferece suporte a associação de padrão de uma instância de serviço com uma determinada sessão. No entanto, diferentes associações baseadas em sessão oferecem suporte a diferentes recursos, além de habilitar o controle de instanciamento baseadas em sessão descrito anteriormente.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]fornece os seguintes tipos de comportamento do aplicativo com base em sessão:  
  
-   O <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> oferece suporte a sessões com base em segurança, em que ambas as extremidades de comunicação concordaram em uma conversa segura específica. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Protegendo serviços](../../../docs/framework/wcf/securing-services.md). Por exemplo, o <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> de associação, que contém suporte para sessões de segurança e sessões confiáveis, por padrão, usa somente uma sessão segura que criptografa e assina digitalmente as mensagens.  
  
-   O <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> associação oferece suporte a sessões baseada em TCP/IP para garantir que todas as mensagens são correlacionadas por conexão no nível de soquete.  
  
-   O <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> elemento, que implementa a especificação WS-ReliableMessaging, fornece suporte para sessões confiáveis em que as mensagens podem ser configuradas para ser entregues em ordem e exatamente uma vez, garantindo que as mensagens são recebidas, mesmo quando as mensagens passam em vários nós durante a conversa. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   O <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> associação fornece sessões de datagrama MSMQ. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> propriedade não especifica o tipo de sessão, o contrato requer, somente que ele requer que um.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Criando um contrato que requer uma sessão  
 Criando um contrato que requer que uma sessão de estados que o grupo de operações que declara o contrato de serviço deve todos ser executado na mesma sessão e que as mensagens devem ser entregues em ordem. Para declarar o nível de suporte de sessão que requer um contrato de serviço, defina o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> sua interface de contrato de serviço ou uma classe para o valor da propriedade de <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> enumeração para especificar se o contrato:  
  
-   Requer uma sessão.  
  
-   Permite que um cliente estabelecer uma sessão.  
  
-   Impede a uma sessão.  
  
 Definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> propriedade, no entanto, especifica o tipo de comportamento baseada em sessão, o contrato requer. Ele instrui o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para confirmar em tempo de execução que o configurado associação (que cria o canal de comunicação) para o serviço, não ou pode estabelecer uma sessão ao implementar um serviço. Novamente, a associação pode atender a esse requisito com qualquer tipo de comportamento baseado em sessão, ele escolhe, de segurança, transporte, confiável ou uma combinação. O comportamento exato depende do <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> valor selecionado. Se a associação configurada do serviço não está de acordo com o valor de <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, uma exceção será lançada. Associações e os canais criarem que suporte a sessões são consideradas baseadas em sessão.  
  
 O contrato de serviço a seguir especifica que todas as operações no `ICalculatorSession` devem ser trocadas dentro de uma sessão. Nenhuma das operações de retorna um valor para o chamador exceto o `Equals` método. No entanto, o `Equals` método não usa nenhum parâmetro e, portanto, só pode retornar um valor diferente de zero dentro de uma sessão em que dados já foi passados para outras operações. Este contrato requer uma sessão para funcionar corretamente. Sem uma sessão associada a um cliente específico, a instância do serviço não tem como saber quais dados anteriores, esse cliente enviou.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Se um serviço permite que uma sessão, em seguida, uma sessão é estabelecida e usada se o cliente inicia um; Caso contrário, nenhuma sessão é estabelecida.  
  
## <a name="sessions-and-service-instances"></a>Sessões e instâncias de serviço  
 Se você usar o padrão de comportamento de instanciação [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], todas as chamadas entre um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto de cliente são tratadas pela mesma instância de serviço. Portanto, no nível do aplicativo, você pode pensar uma sessão como habilitar o comportamento do aplicativo semelhante ao comportamento de chamada local. Por exemplo, quando você cria um objeto local:  
  
-   Um construtor é chamado.  
  
-   Todas as chamadas subsequentes feitas a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] referência de objeto de cliente são processados pela mesma instância de objeto.  
  
-   Um destruidor é chamado quando a referência de objeto é destruída.  
  
 Sessões de habilitar um comportamento semelhante entre clientes e serviços como o comportamento padrão da instância de serviço é usado. Se um contrato de serviço requer ou oferece suporte a sessões, uma ou mais operações do contrato podem ser marcadas como iniciar ou encerrar uma sessão, definindo o <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> e <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> propriedades.  
  
 *Iniciando operações* são aqueles que deve ser chamado como a primeira operação de uma nova sessão. Iniciar operações não pode ser chamado somente após pelo menos uma operação iniciando foi chamada. Portanto, para criar um tipo do construtor de sessão para o serviço declarando iniciante operações projetadas para tirar a entrada de clientes apropriados para o início da instância de serviço. (O estado é associado com a sessão, no entanto e não o objeto de serviço).  
  
 *Finalizando operações*, por outro lado, são aqueles que deve ser chamado em uma sessão existente como a última mensagem de erro. No caso padrão, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] recicla o objeto de serviço e o contexto, depois que a sessão com a qual o serviço estava associado é fechada. Portanto, você pode criar um tipo de destruidor declarando finalizando operações projetadas para executar uma função apropriada ao final da instância do serviço.  
  
> [!NOTE]
>  Embora o comportamento padrão possui uma semelhança locais construtores e destruidores, é somente uma semelhança. Qualquer [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] operação de serviço pode ser um iniciando operação de encerramento ou ambos ao mesmo tempo. Além disso, no caso padrão, iniciando operações pode ser chamado várias vezes em qualquer ordem. Não há sessões adicionais são criadas quando a sessão é estabelecida e associada a uma instância, a menos que você explicitamente controlar o tempo de vida da instância de serviço (manipulando o <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objeto). Por fim, o estado é associado com a sessão e não o objeto de serviço.  
  
 Por exemplo, o `ICalculatorSession` contrato usado no exemplo anterior requer que o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] primeira chamada de objeto de cliente a `Clear` operação antes de qualquer outra operação e que a sessão com isso [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente deve encerrar quando ele chama o `Equals` operação. O exemplo de código a seguir mostra um contrato que impõe esses requisitos. `Clear`deve ser chamado primeiro para iniciar uma sessão, e que a sessão termina quando `Equals` é chamado.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Os serviços não iniciar sessões com clientes. Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos cliente, uma relação direta existe entre o tempo de vida do canal baseadas em sessão e o tempo de vida da sessão em si. Dessa forma, os clientes criar novas sessões, criando novos canais de sessão e subdividir sessões existentes, fechando os canais de sessão normalmente. Um cliente inicia uma sessão com um ponto de extremidade do serviço chamando um dos seguintes:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>o canal retornado por uma chamada para <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>sobre o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] gerado pelo objeto do cliente a [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   Uma operação inicial em ambos os tipos de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente (por padrão, todas as operações estão iniciando). Quando a primeira operação é chamada, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente abre o canal e inicia uma sessão automaticamente.  
  
 Geralmente, um cliente termina uma sessão com um ponto de extremidade do serviço chamando um dos seguintes:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>o canal retornado por uma chamada para <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>sobre o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] gerado pelo Svcutil.exe de objeto de cliente.  
  
-   Uma operação de encerramento em ambos os tipos de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente (por padrão, nenhuma operação está encerrando; o contrato deve especificar explicitamente uma operação de encerramento). Quando a primeira operação é chamada, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objeto cliente abre o canal e inicia uma sessão automaticamente.  
  
 Para obter exemplos, consulte [como: criar um serviço que requer sessões](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) , bem como a [comportamento de serviço padrão](../../../docs/framework/wcf/samples/default-service-behavior.md) e [Instancing](../../../docs/framework/wcf/samples/instancing.md) exemplos.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]os clientes e sessões, consulte [Acessando serviços usando um cliente WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessões de interagem com as configurações do InstanceContext  
 Há uma interação entre o <xref:System.ServiceModel.SessionMode> enumeração em um contrato e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade, que controla a associação entre canais e objetos de serviço específico. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Sessões, instanciação e simultaneidade](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhamento InstanceContext objetos  
 Você também pode controlar qual canal baseadas em sessão ou chamada está associada com a qual <xref:System.ServiceModel.InstanceContext> objeto executando essa associação por conta própria. Para obter um exemplo completo, consulte [InstanceContextSharing](http://msdn.microsoft.com/en-us/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Sessões e Streaming  
 Quando você tiver uma grande quantidade de dados para transferência, o modo de transferência de streaming do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] será uma alternativa viável para o comportamento padrão de buffer e processamento de mensagens na memória em sua totalidade. Você pode obter um comportamento inesperado durante o streaming de chamadas com uma associação baseada em sessão. Todas as chamadas de streaming são feitas por um único canal (o canal de datagrama) que não oferece suporte a sessões mesmo que a associação que está sendo usada esteja configurada para usar sessões. Se vários clientes fazem chamadas para o mesmo objeto de serviço de streaming via uma associação com base em sessão e modo de simultaneidade do objeto de serviço é definido como único e o modo de contexto da instância é definido como `PerSession`, todas as chamadas devem passar pelo canal de datagrama e, portanto apenas uma chamada é processada por vez. Portanto, um ou mais clientes podem atingir o tempo limite. Você pode contornar esse problema definindo o objeto de serviço `InstanceContextMode` para `PerCall` ou simultaneidade a vários.  
  
> [!NOTE]
>  MaxConcurrentSessions não tem efeito nesse caso porque há apenas uma "sessão".  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
