---
title: Utilizando sessões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: a879e90aeab7b40529df1f1a60cd1f879c39720a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143168"
---
# <a name="using-sessions"></a>Utilizando sessões
Nos aplicativos da Windows Communication Foundation (WCF), uma *sessão* correlaciona um grupo de mensagens em uma conversa. As sessões wcf são diferentes do objeto de sessão disponível em ASP.NET aplicativos, suportam diferentes comportamentos e são controladas de diferentes maneiras. Este tópico descreve os recursos que as sessões permitem em aplicativos WCF e como usá-los.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sessões em Aplicativos da Fundação de Comunicação do Windows  
 Quando um contrato de serviço especifica que requer uma sessão, esse contrato está especificando que todas as chamadas (ou seja, as trocas de mensagens subjacentes que suportam as chamadas) devem fazer parte da mesma conversa. Se um contrato especificar que permite sessões, mas não requer uma, os clientes podem se conectar e estabelecer uma sessão ou não estabelecer uma sessão. Se a sessão terminar e uma mensagem for enviada pelo mesmo canal, uma exceção será lançada.  
  
 As sessões de WCF têm as seguintes características conceituais principais:  
  
- Eles são explicitamente iniciados e encerrados pelo aplicativo de chamada (o cliente WCF).  
  
- As mensagens entregues durante uma sessão são processadas na ordem em que são recebidas.  
  
- As sessões correlacionam um grupo de mensagens em uma conversa. Diferentes tipos de correlação são possíveis. Por exemplo, um canal baseado em sessão pode correlacionar mensagens com base em uma conexão de rede compartilhada, enquanto outro canal baseado em sessão pode correlacionar mensagens com base em uma tag compartilhada no corpo de mensagens. As características que podem ser derivadas da sessão dependem da natureza da correlação.  
  
- Não há um armazenamento geral de dados associado a uma sessão wcf.  
  
 Se você estiver <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> familiarizado com a classe em ASP.NET aplicativos e a funcionalidade que ele fornece, você pode notar as seguintes diferenças entre esse tipo de sessão e sessões de WCF:  
  
- ASP.NET sessões são sempre iniciadas pelo servidor.  
  
- ASP.NET sessões são implicitamente desordenadas.  
  
- ASP.NET sessões fornecem um mecanismo geral de armazenamento de dados entre as solicitações.  
  
 Este tópico descreve:  
  
- O comportamento de execução padrão ao usar vinculações baseadas em sessão na camada do modelo de serviço.  
  
- Os tipos de recursos que as vinculações fornecidas por sessão wcf, fornecidas pelo sistema.  
  
- Como criar um contrato que declare um requisito de sessão.  
  
- Como entender e controlar a criação e o término da sessão e a relação da sessão com a instância de serviço.  
  
## <a name="default-execution-behavior-using-sessions"></a>Comportamento de execução padrão usando sessões  
 Uma vinculação que tenta iniciar uma sessão é chamada de vinculação *baseada em sessão.* Os contratos de serviço especificam que eles exigem, permitem <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ou recusam vinculações baseadas em sessão, definindo a propriedade na interface (ou classe) do contrato de serviço para um dos valores de <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> enumeração. Por padrão, o valor <xref:System.ServiceModel.SessionMode.Allowed>dessa propriedade é , o que significa que se um cliente usa uma vinculação baseada em sessão com uma implementação de serviço WCF, o serviço estabelece e usa a sessão fornecida.  
  
 Quando um serviço WCF aceita uma sessão de cliente, os seguintes recursos são ativados por padrão:  
  
1. Todas as chamadas entre um objeto cliente WCF são tratadas pela mesma instância de serviço.  
  
2. Diferentes vinculações baseadas em sessão fornecem recursos adicionais.  
  
## <a name="system-provided-session-types"></a>Tipos de sessão fornecidos pelo sistema  
 Uma vinculação baseada em sessão suporta a associação padrão de uma instância de serviço com uma sessão específica. No entanto, diferentes vinculações baseadas em sessão suportam diferentes recursos, além de habilitar o controle de instancing baseado em sessão descrito anteriormente.  
  
 O WCF fornece os seguintes tipos de comportamento de aplicativo baseado em sessão:  
  
- O <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> suporte a sessões baseadas em segurança, nas quais ambas as extremidades da comunicação concordaram com uma conversa segura específica. Para obter mais informações, consulte [Protegendo serviços](securing-services.md). Por exemplo, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> a vinculação, que contém suporte para sessões de segurança e sessões confiáveis, por padrão usa apenas uma sessão segura que criptografa e assina digitalmente mensagens.  
  
- A <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> vinculação suporta sessões baseadas em TCP/IP para garantir que todas as mensagens estejam correlacionadas pela conexão no nível do soquete.  
  
- O <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> elemento, que implementa a especificação WS-ReliableMessaging, fornece suporte para sessões confiáveis nas quais as mensagens podem ser configuradas para serem entregues em ordem e exatamente uma vez, garantindo que as mensagens sejam recebidas mesmo quando as mensagens viajam através de vários nós durante a conversa. Para obter mais informações, consulte [Sessões Confiáveis](./feature-details/reliable-sessions.md).  
  
- A <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> vinculação fornece sessões de datagram do MSMQ. Para obter mais informações, consulte [Filas no WCF](./feature-details/queues-in-wcf.md).  
  
 A <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> definição da propriedade não especifica o tipo de sessão que o contrato requer, apenas que requer uma.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Criando um contrato que requer uma sessão  
 A criação de um contrato que exija uma sessão afirma que o grupo de operações que o contrato de serviço declara deve ser executado dentro da mesma sessão e que as mensagens devem ser entregues em ordem. Para afirmar o nível de suporte de sessão <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> que um contrato de serviço exige, <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> defina a propriedade na interface ou classe do contrato de serviço para o valor da enumeração para especificar se o contrato:  
  
- Requer uma sessão.  
  
- Permite que um cliente estabeleça uma sessão.  
  
- Proíbe uma sessão.  
  
 A <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> definição da propriedade, no entanto, não especifica o tipo de comportamento baseado em sessão que o contrato exige. Ele instrui o WCF a confirmar em tempo de execução que a vinculação configurada (que cria o canal de comunicação) para o serviço não faz, ou pode estabelecer uma sessão ao implementar um serviço. Novamente, a vinculação pode satisfazer esse requisito com qualquer tipo de comportamento baseado em sessão que ele escolher — segurança, transporte, confiável ou alguma combinação. O comportamento exato depende <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> do valor selecionado. Se a vinculação configurada do serviço não <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>estiver em conformidade com o valor de , uma exceção será lançada. As vinculações e os canais que eles criam dizem ser baseados em sessões.  
  
 O contrato de serviço a seguir `ICalculatorSession` especifica que todas as operações no deve ser trocada dentro de uma sessão. Nenhuma das operações retorna um valor `Equals` ao chamador, exceto o método. No entanto, o `Equals` método não tem parâmetros e, portanto, só pode retornar um valor não-zero dentro de uma sessão em que os dados já foram passados para as outras operações. Este contrato requer uma sessão para funcionar corretamente. Sem uma sessão associada a um cliente específico, a instância de serviço não tem como saber quais dados anteriores esse cliente enviou.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Se um serviço permitir uma sessão, uma sessão será estabelecida e usada se o cliente iniciar uma; caso contrário, nenhuma sessão é estabelecida.  
  
## <a name="sessions-and-service-instances"></a>Sessões e Instâncias de Serviço  
 Se você usar o comportamento de insporto padrão no WCF, todas as chamadas entre um objeto cliente WCF serão tratadas pela mesma instância de serviço. Portanto, no nível de aplicação, você pode pensar em uma sessão como habilitando o comportamento do aplicativo semelhante ao comportamento de chamada local. Por exemplo, quando você cria um objeto local:  
  
- Um construtor é chamado.  
  
- Todas as chamadas subseqüentes feitas à referência de objeto cliente WCF são processadas pela mesma instância de objeto.  
  
- Um destruidor é chamado quando a referência do objeto é destruída.  
  
 As sessões permitem um comportamento semelhante entre clientes e serviços, desde que o comportamento padrão da instância de serviço seja usado. Se um contrato de serviço exigir ou apoiar sessões, uma ou mais operações de contrato <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> podem ser marcadas como iniciando ou terminando uma sessão definindo as propriedades.  
  
 *As operações iniciantes* são aquelas que devem ser chamadas como a primeira operação de uma nova sessão. Iniciar operações não pode ser chamado somente após pelo menos uma operação iniciando foi chamada. Portanto, você pode criar uma espécie de construtor de sessão para o seu serviço, declarando iniciar operações projetadas para receber a entrada de clientes apropriados para o início da instância de serviço. (O estado está associado à sessão, no entanto, e não ao objeto de serviço.)  
  
 *As operações de término,* por outro lado, são aquelas que devem ser chamadas como a última mensagem em uma sessão existente. Em casos padrão, WCF recicla o objeto de serviço e seu contexto após a sessão com que o serviço foi associado é fechada. Você pode, portanto, criar uma espécie de destruidor declarando operações terminadas projetadas para executar uma função apropriada ao final da instância de serviço.  
  
> [!NOTE]
> Embora o comportamento padrão tenha uma semelhança com construtores e destruidores locais, é apenas uma semelhança. Qualquer operação de serviço WCF pode ser uma operação de início ou término, ou ambas ao mesmo tempo. Além disso, no caso padrão, as operações de início podem ser chamadas várias vezes em qualquer ordem; nenhuma sessão adicional é criada uma vez que a sessão é estabelecida e associada a uma instância, a menos que você controle explicitamente a vida útil da instância de serviço (manipulando o <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objeto). Finalmente, o estado está associado à sessão e não ao objeto de serviço.  
  
 Por exemplo, `ICalculatorSession` o contrato usado no exemplo anterior exige que `Clear` o objeto cliente WCF ligue primeiro para a operação antes `Equals` de qualquer outra operação e que a sessão com este objeto cliente WCF deve terminar quando ele chamar a operação. O exemplo de código a seguir mostra um contrato que impõe esses requisitos. `Clear`deve ser chamado primeiro para iniciar uma `Equals` sessão, e essa sessão termina quando é chamada.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Os serviços não iniciam sessões com clientes. Nos aplicativos clientes WCF, existe uma relação direta entre a vida útil do canal baseado em sessão e a vida útil da própria sessão. Como tal, os clientes criam novas sessões criando novos canais baseados em sessões e desembaindo as sessões existentes fechando canais baseados em sessões graciosamente. Um cliente inicia uma sessão com um ponto final de serviço ligando para um dos seguintes:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>no canal retornou por <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>uma chamada para .  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>no objeto cliente WCF gerado pela [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Uma operação de início em qualquer tipo de objeto cliente WCF (por padrão, todas as operações estão afiando). Quando a primeira operação é chamada, o objeto cliente WCF abre automaticamente o canal e inicia uma sessão.  
  
 Normalmente, um cliente termina uma sessão com um ponto final de serviço ligando para um dos seguintes:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>no canal retornou por <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>uma chamada para .  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>sobre o objeto cliente WCF gerado por Svcutil.exe.  
  
- Uma operação de término em qualquer tipo de objeto cliente WCF (por padrão, nenhuma operação está terminando; o contrato deve especificar explicitamente uma operação de rescisão). Quando a primeira operação é chamada, o objeto cliente WCF abre automaticamente o canal e inicia uma sessão.  
  
 Por exemplo, [veja Como: Criar um serviço que exija sessões,](./feature-details/how-to-create-a-service-that-requires-sessions.md) bem como as amostras [de Comportamento de Serviço Padrão](./samples/default-service-behavior.md) e [Instancing.](./samples/instancing.md)  
  
 Para obter mais informações sobre clientes e sessões, consulte [Serviços de acesso usando um cliente WCF](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>As sessões interagem com as configurações do contexto de instância  
 Há uma interação <xref:System.ServiceModel.SessionMode> entre a enumeração <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> em um contrato e o imóvel, que controla a associação entre canais e objetos de serviço específicos. Para obter mais informações, consulte [Sessões, Instancing e Concurrency](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Compartilhando objetos de contexto de instância  
 Você também pode controlar qual canal ou chamada <xref:System.ServiceModel.InstanceContext> baseado em sessão está associado a qual objeto realizando essa associação você mesmo.
  
## <a name="sessions-and-streaming"></a>Sessões e Streaming  
 Quando você tem uma grande quantidade de dados para transferir, o modo de transferência de streaming no WCF é uma alternativa viável ao comportamento padrão de buffering e processamento de mensagens na memória em sua totalidade. Você pode obter um comportamento inesperado durante o streaming de chamadas com uma associação baseada em sessão. Todas as chamadas de streaming são feitas por um único canal (o canal de datagrama) que não oferece suporte a sessões mesmo que a associação que está sendo usada esteja configurada para usar sessões. Se vários clientes fizerem chamadas de streaming para o mesmo objeto de serviço durante uma vinculação baseada em `PerSession`sessão e o modo de simultâneo do objeto de serviço estiver definido como único e seu modo de contexto de instância estiver definido para, todas as chamadas devem passar pelo canal de datagram e, portanto, apenas uma chamada é processada por vez. Um ou mais clientes podem, então, cronometrados. Você pode contornar esse problema definindo o `InstanceContextMode` `PerCall` objeto de serviço para ou Concurrency para vários.  
  
> [!NOTE]
> MaxConcurrentSessions não tem efeito neste caso porque há apenas uma "sessão" disponível.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
