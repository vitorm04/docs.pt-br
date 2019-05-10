---
title: Utilizando sessões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: fc0bfec95e625c1433636fbe5e0fdb6cc1112b14
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645151"
---
# <a name="using-sessions"></a>Utilizando sessões
Em aplicativos do Windows Communication Foundation (WCF), uma *sessão* correlaciona a um grupo de mensagens em uma conversa. As sessões WCF são diferentes do objeto de sessão disponível no [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplicativos, dar suporte a comportamentos diferentes e são controlados de maneiras diferentes. Este tópico descreve os recursos que permitem que as sessões no WCF aplicativos e como usá-los.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sessões em aplicativos do Windows Communication Foundation  
 Quando um contrato de serviço Especifica que exige uma sessão, esse contrato é Especifica que todas as chamadas (ou seja, as subjacente trocas de mensagens que oferecem suporte as chamadas) devem ser parte da mesma conversa. Se um contrato especifica que ele permite que as sessões, mas não exige um, os clientes podem se conectar e a estabelecer uma sessão ou não estabelecer uma sessão. Se a sessão termina e uma mensagem é enviada por meio do mesmo canal de que uma exceção será lançada.  
  
 As sessões WCF têm os seguintes recursos de conceituais principais:  
  
- Eles são explicitamente iniciados e encerrados pelo aplicativo de chamada (o cliente do WCF).  
  
- Mensagens entregues durante uma sessão são processadas na ordem em que elas são recebidas.  
  
- Sessões de correlação um grupo de mensagens em uma conversa. Diferentes tipos de correlação são possíveis. Por exemplo, um canal com base em sessão pode correlacionar mensagens com base em uma conexão de rede compartilhado, enquanto outro canal com base em sessão pode correlacionar mensagens com base em uma marca compartilhada no corpo da mensagem. Os recursos que podem ser derivados da sessão dependem da natureza da correlação.  
  
- Não há nenhum armazenamento de dados gerais associado com uma sessão do WCF.  
  
 Se você estiver familiarizado com o <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> classe [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplicativos e a funcionalidade que ele fornece, você pode observar as seguintes diferenças entre esse tipo de sessão e as sessões WCF:  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] as sessões são sempre iniciadas pelo servidor.  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] as sessões são implicitamente não ordenadas.  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] as sessões fornecem um mecanismo de armazenamento de dados geral em todas as solicitações.  
  
 Este tópico descreve:  
  
- O comportamento de execução padrão ao usar associações de sessão com base na camada de modelo de serviço.  
  
- Os tipos de recursos que oferecem as associações do WCF com base em sessão, fornecida pelo sistema.  
  
- Como criar um contrato que declara um requisito de sessão.  
  
- Como entender e controlar a criação e o encerramento da sessão e a relação da sessão para a instância do serviço.  
  
## <a name="default-execution-behavior-using-sessions"></a>Usando sessões de comportamento de execução padrão  
 Uma associação que tenta iniciar uma sessão é chamada de um *baseadas em sessão* associação. Contratos de serviço especificam que eles exigem, permitem ou recusam associações baseadas em sessão, definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade na interface de contrato de serviço (ou classe) para um do <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> valores de enumeração. Por padrão, o valor dessa propriedade é <xref:System.ServiceModel.SessionMode.Allowed>, o que significa que, se um cliente usa uma associação baseada em sessão com uma implementação de serviço do WCF, o serviço estabelece e usa a sessão fornecida.  
  
 Quando um serviço WCF aceita uma sessão de cliente, os seguintes recursos são habilitados por padrão:  
  
1. Todas as chamadas entre um objeto de cliente do WCF são manipuladas pela mesma instância de serviço.  
  
2. Associações diferentes com base em sessão fornecem recursos adicionais.  
  
## <a name="system-provided-session-types"></a>Tipos de sessão fornecido pelo sistema  
 Uma associação baseada em sessão oferece suporte a associação de padrão de uma instância de serviço com uma determinada sessão. No entanto, ligações diferentes com base em sessão de suportam a recursos diferentes, além de habilitar o controle de instanciação baseadas em sessão descrito anteriormente.  
  
 O WCF fornece os seguintes tipos de comportamento do aplicativo com base em sessão:  
  
- O <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> dá suporte a sessões com base em segurança, em que ambas as extremidades de comunicação concordamos uma conversa segura específica. Para obter mais informações, consulte [protegendo serviços](../../../docs/framework/wcf/securing-services.md). Por exemplo, o <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> de associação, que contém suporte para sessões de segurança e sessões confiáveis, por padrão usa somente uma sessão segura que criptografa e assina digitalmente as mensagens.  
  
- O <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> associação dá suporte a sessões baseadas em TCP/IP para garantir que todas as mensagens são correlacionadas pela conexão no nível de soquete.  
  
- O <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> elemento, que implementa a especificação de WS-ReliableMessaging, fornece suporte para sessões confiáveis em que as mensagens podem ser configuradas para ser entregues em ordem e exatamente uma vez, garantindo que as mensagens são recebidas, mesmo quando as mensagens passam em vários nós durante a conversa. Para obter mais informações, consulte [sessões confiáveis](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
- O <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> associação fornece sessões de datagrama do MSMQ. Para obter mais informações, consulte [filas no WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> propriedade não especifica o tipo de sessão, o contrato requer, somente que ele requer um.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Criando um contrato que requer uma sessão  
 Criando um contrato que requer que uma sessão declara que o grupo de operações que declara o contrato de serviço deve todos ser executado na mesma sessão, e que as mensagens devem ser entregues em ordem. Para declarar o nível de suporte de sessão que requer um contrato de serviço, defina as <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> propriedade em sua interface de contrato de serviço ou uma classe para o valor da <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> enumeração para especificar se o contrato:  
  
- Requer uma sessão.  
  
- Permite que um cliente estabelecer uma sessão.  
  
- Proíbe a uma sessão.  
  
 Definindo o <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> propriedade, no entanto, especifica o tipo de comportamento baseada em sessão, o contrato requer. Ele instrui o WCF para confirmar em tempo de execução que o configurado associação (que cria o canal de comunicação) para o serviço faz, não faz isso ou pode estabelecer uma sessão ao implementar um serviço. Novamente, a associação pode atender a esse requisito com qualquer tipo de comportamento baseado em sessão, ele escolhe — segurança, transporte, confiável ou alguma combinação. O comportamento exato depende do <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> valor selecionado. Se a associação configurada do serviço não estiver de acordo com o valor de <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, uma exceção será lançada. Associações e os canais que eles criam que suporte sessões devem ser baseadas em sessão.  
  
 O contrato de serviço a seguir especifica que todas as operações no `ICalculatorSession` devem ser trocados dentro de uma sessão. Nenhuma das operações retorna um valor para o chamador, exceto o `Equals` método. No entanto, o `Equals` método não usa nenhum parâmetro e, portanto, só pode retornar um valor diferente de zero dentro de uma sessão na qual os dados já tiverem sido passados para as outras operações. Esse contrato exige uma sessão para funcionar corretamente. Sem uma sessão associada a um cliente específico, a instância do serviço não tem como saber quais dados anteriores esse cliente enviou.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Se um serviço permite que uma sessão, em seguida, uma sessão é estabelecida e usada se o cliente inicia um; Caso contrário, nenhuma sessão for estabelecida.  
  
## <a name="sessions-and-service-instances"></a>Sessões e instâncias de serviço  
 Se você usar o padrão de comportamento no WCF de instâncias, todas as chamadas entre um objeto de cliente do WCF são tratadas pela mesma instância de serviço. Portanto, no nível do aplicativo, você pode pensar uma sessão como habilitar o comportamento do aplicativo semelhante ao comportamento da chamada local. Por exemplo, quando você cria um objeto local:  
  
- Um construtor é chamado.  
  
- Todas as chamadas subsequentes feitas para a referência de objeto de cliente do WCF são processadas pela mesma instância do objeto.  
  
- Um destruidor é chamado quando a referência de objeto é destruída.  
  
 As sessões permitem um comportamento semelhante entre clientes e serviços, desde que o comportamento de instância de serviço padrão é usado. Se um contrato de serviço requer ou dá suporte a sessões, uma ou mais operações de contrato podem ser marcadas como iniciar ou encerrar uma sessão, definindo o <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> e <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> propriedades.  
  
 *Iniciando operações* são aqueles que deve ser chamado como a primeira operação de uma nova sessão. Iniciar operações não pode ser chamado somente após pelo menos uma operação iniciando foi chamada. Portanto, você pode criar um tipo de construtor da sessão para seu serviço, declarando iniciante operações projetadas para tirar a entrada de clientes apropriados para o início da instância do serviço. (O estado é associado com a sessão, no entanto e não o objeto de serviço).  
  
 *Finalizando operações*, por outro lado, são aqueles que deve ser chamado como a última mensagem em uma sessão existente. Em casos padrão, WCF recicla o objeto de serviço e seu contexto após a sessão com que o serviço foi associado é fechada. Portanto, você pode criar um tipo de destruidor, declarando terminação operações projetadas para executar uma função apropriada para o final da instância do serviço.  
  
> [!NOTE]
>  Embora o comportamento padrão é responsável por uma semelhança com locais construtores e destruidores, é apenas uma semelhança. Qualquer operação de serviço WCF pode ser um iniciando operação de terminação ou ambos ao mesmo tempo. Além disso, no caso padrão, inicialização de operações pode ser chamado qualquer número de vezes em qualquer ordem. Não há sessões adicionais serão criados depois que a sessão é estabelecida e associada a uma instância, a menos que você controla explicitamente o tempo de vida da instância do serviço (por meio da manipulação de <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objeto). Por fim, o estado é associado com a sessão e não o objeto de serviço.  
  
 Por exemplo, o `ICalculatorSession` contrato usado no exemplo anterior requer que o cliente WCF objeto primeira chamada a `Clear` operação antes de qualquer outra operação e que a sessão com esse objeto de cliente do WCF deve ser interrompido quando ele chama o `Equals` operação. O exemplo de código a seguir mostra um contrato que impõe a esses requisitos. `Clear` deve ser chamado primeiro para iniciar uma sessão, e que a sessão termina quando `Equals` é chamado.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Os serviços não iniciam as sessões com clientes. Em aplicativos de cliente do WCF, existe uma relação direta entre o tempo de vida do canal com base em sessão e o tempo de vida da sessão em si. Dessa forma, os clientes criar novas sessões, criando novos canais com base em sessão e subdividir sessões existentes, fechando canais com base em sessão normalmente. Um cliente inicia uma sessão com um ponto de extremidade de serviço chamando um dos seguintes:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> no canal retornado por uma chamada para <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> no objeto de cliente WCF gerado pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Uma operação de iniciante em qualquer tipo de objeto de cliente do WCF (por padrão, todas as operações estão iniciando). Quando a primeira operação é chamada, o objeto de cliente WCF abre o canal automaticamente e inicia uma sessão.  
  
 Normalmente, um cliente termina uma sessão com um ponto de extremidade de serviço chamando um dos seguintes:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> no canal retornado por uma chamada para <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> no objeto de cliente WCF gerado pelo Svcutil.exe.  
  
- Uma operação de terminação em qualquer tipo de objeto de cliente do WCF (por padrão, nenhuma operação está encerrando; o contrato deve especificar explicitamente uma operação de terminação). Quando a primeira operação é chamada, o objeto de cliente WCF abre o canal automaticamente e inicia uma sessão.  
  
 Para ver mais exemplos, veja [Como: Criar um serviço que requer sessões](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) , bem como a [padrão de comportamento de serviço](../../../docs/framework/wcf/samples/default-service-behavior.md) e [criação de instâncias](../../../docs/framework/wcf/samples/instancing.md) exemplos.  
  
 Para obter mais informações sobre os clientes e sessões, consulte [serviços de acesso usando um cliente WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessões de interagem com as configurações de InstanceContext  
 Há uma interação entre o <xref:System.ServiceModel.SessionMode> enumeração em um contrato e o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> propriedade, que controla a associação entre canais e objetos de serviço específico. Para obter mais informações, consulte [sessões, criação de instâncias e simultaneidade](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhando objetos InstanceContext  
 Você também pode controlar qual canal com base em sessão ou chamada está associada com a qual <xref:System.ServiceModel.InstanceContext> objeto executando essa associação por conta própria. 
  
## <a name="sessions-and-streaming"></a>Sessões e Streaming  
 Quando você tiver uma grande quantidade de dados a serem transferidos, o modo de transferência de streaming no WCF é uma alternativa viável para o comportamento padrão do buffer e processamento de mensagens na memória em sua totalidade. Você pode obter um comportamento inesperado durante o streaming de chamadas com uma associação baseada em sessão. Todas as chamadas de streaming são feitas por um único canal (o canal de datagrama) que não oferece suporte a sessões mesmo que a associação que está sendo usada esteja configurada para usar sessões. Se vários clientes fizerem chamadas de streaming para o mesmo objeto ao longo de uma associação baseada em sessão e modo de simultaneidade do objeto de serviço é definido como único e seu modo de contexto de instância é definido como `PerSession`, todas as chamadas deverão passar pelo canal de datagrama e, portanto, apenas uma chamada é processada por vez. Portanto, um ou mais clientes podem atingir o tempo limite. Você pode contornar esse problema definindo o objeto de serviço `InstanceContextMode` para `PerCall` ou simultaneidade como múltipla.  
  
> [!NOTE]
>  MaxConcurrentSessions não tem efeito nesse caso porque há apenas uma "sessão" disponível.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
