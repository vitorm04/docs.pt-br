---
title: Escolhendo um padrão de troca de mensagens
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 98788fb89fc68dc1220d9bf8d9ad89df5ca69e6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157715"
---
# <a name="choosing-a-message-exchange-pattern"></a>Escolhendo um padrão de troca de mensagens
A primeira etapa ao escrever um transporte personalizado é decidir qual *padrões de troca de mensagem* (ou MEPs) são necessários para o canal que você está desenvolvendo. Este tópico descreve as opções disponíveis e discute os vários requisitos. Isso é a primeira tarefa na lista de tarefas de desenvolvimento canal descrita em [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Seis padrões de troca de mensagem  
 Há três MEPs à sua escolha:  
  
-   Datagrama (<xref:System.ServiceModel.Channels.IInputChannel> e <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Ao usar um datagrama MEP, um cliente envia uma mensagem usando um *disparar e esquecer* exchange. A disparar e esquecer exchange é aquela que requer a confirmação de out-of-band de entrega bem-sucedida. A mensagem poderá ser perdida em trânsito e nunca alcançar o serviço. Se a operação de envio for concluído com êxito no lado do cliente, ele não garante que o ponto de extremidade remoto recebeu a mensagem. O datagrama é um bloco de construção fundamental para mensagens, como você pode criar seus próprios protocolos nela — incluindo protocolos confiáveis e segura. Implementam canais de datagrama de cliente a <xref:System.ServiceModel.Channels.IOutputChannel> canais de datagrama de interface e o serviço de implementam o <xref:System.ServiceModel.Channels.IInputChannel> interface.  
  
-   Solicitação-resposta (<xref:System.ServiceModel.Channels.IRequestChannel> e <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     Neste MEP, uma mensagem é enviada e uma resposta é recebida. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador GET solicitações. Esse padrão também é conhecido como half-duplex. Este MEP, canais de cliente implementam <xref:System.ServiceModel.Channels.IRequestChannel> e implementam canais de serviço <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplex (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     O MEP duplex permite que um número arbitrário de mensagens a serem enviadas por um cliente e recebidos em qualquer ordem. O MEP duplex é como uma conversa de telefone, em que cada palavra que está sendo falada é uma mensagem. Porque ambos os lados podem enviar e receber essa MEP, a interface implementada por canais de cliente e o serviço é <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Os três padrões de troca de mensagens básicas. De cima para baixo: datagrama, solicitação-resposta e duplex.  
  
 Cada uma dessas MEPs também pode dar suporte *sessões*. Uma sessão (e a implementação de <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> do tipo <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) correlaciona todas as mensagens enviadas e recebidas em um canal. O padrão de solicitação-resposta é uma sessão de duas mensagens autônoma, como a solicitação e resposta são correlacionadas. Em contraste, o padrão de solicitação-resposta que dá suporte a sessões implica que todos os pares de solicitação/resposta naquele canal estão correlacionados entre si. Isso lhe dá um total de seis MEPs à sua escolha:  
  
-   Datagrama  
  
-   Solicitação-resposta  
  
-   Duplex  
  
-   Datagrama com sessões  
  
-   Solicitação-resposta com sessões  
  
-   Duplex com sessões  
  
> [!NOTE]
>  Para o transporte UDP, o MEP única com suporte é datagrama, porque é inerentemente um incêndio e se esqueça de protocolo UDP.  
  
## <a name="sessions-and-sessionful-channels"></a>Sessões e canais de sessão  
 No mundo do sistema de rede, há protocolos de conexão-oriented (por exemplo, TCP) e sem conexão (por exemplo, UDP). O WCF usa a sessão de termo para significar uma abstração de lógica de conexão semelhante. Protocolos WCF de sessão são semelhantes aos protocolos de rede orientados a conexão e protocolos do WCF sem sessão são semelhantes aos protocolos de rede sem conexão.  
  
 No modelo de objeto de canal, cada sessão lógica se manifesta como uma instância de um canal de sessão. Portanto, cada sessão nova criada pelo cliente e aceito no serviço, corresponde a um novo canal de sessão em cada lado. A diagrama a seguir mostra, na parte superior, a estrutura de canais sem sessão e, na parte inferior, a estrutura de canais de sessão.  
  
 ![Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Um cliente cria um novo canal de sessão e envia uma mensagem. No lado do serviço, o ouvinte de canais recebe essa mensagem e detecta que ele pertence a uma nova sessão para que ele cria um novo canal de sessão e entrega-o para o aplicativo (em resposta ao aplicativo que está chamando AcceptChannel no ouvinte de canal). O aplicativo, em seguida, recebe essa mensagem e todas as mensagens subsequentes, enviadas na mesma sessão por meio do mesmo canal de sessão.  
  
 Outro cliente (ou mesmo cliente) cria uma nova sessão e envia uma mensagem. O ouvinte de canais detecta essa mensagem está em uma nova sessão e cria um novo canal de sessão e o processo se repete.  
  
 Sem sessões, não há nenhuma correlação entre canais e sessões. Portanto, um ouvinte de canais cria apenas um canal por meio do qual todas as mensagens recebidas são entregues ao aplicativo. Além disso, não há nenhuma mensagem ordenação porque não há nenhuma sessão na qual você deseja manter a ordem das mensagens. A parte superior do gráfico anterior ilustra uma troca de mensagens sem sessão.  
  
## <a name="starting-and-terminating-sessions"></a>Iniciar e encerrar as sessões  
 Sessões são iniciadas no cliente, simplesmente criando um novo canal de sessão. Eles são iniciados no serviço quando o serviço recebe uma mensagem que foi enviada em uma nova sessão. Da mesma forma, as sessões sejam encerradas por fechar ou anular um canal de sessão.  
  
 A exceção a isso é <xref:System.ServiceModel.Channels.IDuplexSessionChannel> que é usado para enviar e receber mensagens em um padrão de sessão de comunicação duplex. É possível que um dos lados deve interromper o envio de mensagens, mas continuar a receber mensagens, portanto, ao usar <xref:System.ServiceModel.Channels.IDuplexSessionChannel> há um mecanismo que permite que você feche a sessão de saída indicando não enviará mais mensagens, mas manter a sessão de entrada aberta, permitindo que você continue a receber mensagens.  
  
 Em geral, as sessões são fechadas do lado de saída e não o lado de entrada. Ou seja, canais de sessão de saída podem ser fechados, claramente, assim, encerrando a sessão. Fechar um canal de saída de sessão faz com que o canal de entrada sessão correspondente retornar nulo para a aplicativo que chama <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> sobre o <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 No entanto canais de sessão de entrada não devem ser fechado, a menos que <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> sobre o <xref:System.ServiceModel.Channels.IDuplexSessionChannel> retorna nulo, indicando que a sessão já está fechada. Se <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> sobre o <xref:System.ServiceModel.Channels.IDuplexSessionChannel> tem não retornou nulo, fechar um canal de sessão de entrada pode lançar uma exceção porque ele pode receber mensagens inesperadas durante o fechamento. Se desejar que um receptor finalizar uma sessão antes do remetente, ele deverá chamar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> no canal de entrada, que encerra a sessão abruptamente.  
  
## <a name="writing-sessionful-channels"></a>Canais de sessão de gravação  
 Como um autor de canal de sessão, há algumas coisas que o canal deve fazer para fornecer as sessões. No lado do envio, seu canal precisa:  
  
-   Para cada novo canal, crie uma nova sessão e associá-lo a uma nova id de sessão que é uma cadeia de caracteres exclusiva. Ou obtenha uma nova sessão do canal de sessão abaixo, você na pilha.  
  
-   Para cada mensagem enviada usando este canal, se o seu canal criou a sessão (em vez de obtenção da camada abaixo, você), você precisará associar a mensagem com a sessão. Para os canais de protocolo, isso normalmente é feito adicionando um cabeçalho SOAP. Para os canais de transporte, isso normalmente é feito criando uma nova conexão de transporte ou adicionando informações de sessão para o protocolo de enquadramento.  
  
-   Para cada mensagem enviada usando este canal, você precisa fornecer as garantias de entrega mencionadas acima. Se você está confiando no canal abaixo, você para fornecer a sessão, esse canal também fornecerá as garantias de entrega. Se você está fornecendo a sessão, você precisará implementar essas garantias como parte de seu protocolo. Em geral, se você estiver escrevendo um canal do protocolo que supõe que o WCF em ambos os lados podem exigir o transporte TCP ou o canal de mensagens confiáveis e contar com qualquer um para fornecer uma sessão.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> é chamado em seu canal, execute o trabalho necessário para fechar a sessão usando o tempo limite especificado ou padrão. Isso pode ser tão simple quanto chamar <xref:System.ServiceModel.ICommunicationObject.Close%2A> no canal abaixo (se você obteve apenas a sessão dele) ou enviando uma mensagem SOAP especial ou fechar uma conexão de transporte.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> é chamado em seu canal, encerrar a sessão abruptamente sem executar e/s. Isso pode significar fazendo nada ou pode envolver anular uma conexão de rede ou algum outro recurso.  
  
 No lado do recebimento, o canal precisa:  
  
-   Para cada mensagem de entrada, o ouvinte de canais deve detectar a sessão que pertence. Se esta for a primeira mensagem na sessão, o ouvinte de canais deve criar um novo canal e retorná-lo da chamada para <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. Caso contrário, o ouvinte de canais deve localizar o canal existente que corresponde à sessão e entrega a mensagem por meio desse canal.  
  
-   Se o canal está fornecendo a sessão (junto com as garantias de entrega necessária) o lado de recebimento talvez precise executar algumas ações, como mensagens reordenar ou enviar confirmações.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Close%2A> é chamado em seu canal, execute o trabalho necessário para fechar a sessão, o tempo limite especificado ou padrão. Isso pode resultar em exceções se o canal recebe uma mensagem enquanto aguarda o tempo limite de fechamento expirar. Isso ocorre porque o canal estará no estado de fechamento quando ele recebe uma mensagem para que ela lançaria.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> é chamado em seu canal, encerrar a sessão abruptamente sem executar e/s. Novamente, isso pode significar fazendo nada ou pode envolver anular uma conexão de rede ou algum outro recurso.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md)
