---
title: Escolhendo um padrão de troca de mensagens
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: ac5ff841eb4e314c1c9d04c895d7a22766da003e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805883"
---
# <a name="choosing-a-message-exchange-pattern"></a>Escolhendo um padrão de troca de mensagens
A primeira etapa na composição de um transporte personalizado é decidir qual *padrões de troca de mensagens* (ou MEPs) são necessários para o canal que você está desenvolvendo. Este tópico descreve as opções disponíveis e aborda os diversos requisitos. Essa é a primeira tarefa na lista de tarefas de desenvolvimento canal descrita em [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Seis padrões de troca de mensagem  
 Há três MEPs à sua escolha:  
  
-   Datagrama (<xref:System.ServiceModel.Channels.IInputChannel> e <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Ao usar um datagrama MEPS, um cliente envia uma mensagem usando um *disparar e esquecer* exchange. Um disparar e esquecer exchange é aquela que requer confirmação fora de banda de entrega bem-sucedida. A mensagem pode ser perdido em trânsito e nunca alcançar o serviço. Se a operação de envio for concluído com êxito no lado do cliente, ele não garante que o ponto de extremidade remoto recebeu a mensagem. O datagrama é um componente fundamental para mensagens, como você pode criar seus próprios protocolos sobre ele — incluindo protocolos confiáveis e seguro. Canais de datagrama do cliente implementam a <xref:System.ServiceModel.Channels.IOutputChannel> canais de datagrama de interface e o serviço implementam o <xref:System.ServiceModel.Channels.IInputChannel> interface.  
  
-   Solicitação-resposta (<xref:System.ServiceModel.Channels.IRequestChannel> e <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     Neste MEPS, uma mensagem é enviada, e uma resposta é recebida. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador GET solicitações. Esse padrão também é conhecido como half-duplex. Este MEPS canais de cliente implementam <xref:System.ServiceModel.Channels.IRequestChannel> e canais de serviço implementam <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplex (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     O MEPS duplex permite que um número arbitrário de mensagens sejam enviadas por um cliente e recebidos em qualquer ordem. O duplex MEPS é como uma conversa telefônica, onde cada palavra que está sendo falada é uma mensagem. Como ambos os lados podem enviar e receber este MEPS, a interface implementada por canais de cliente e de serviço é <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Os três padrões de troca de mensagem básica. Cima para baixo: datagrama, solicitação / resposta e duplex.  
  
 Cada um desses MEPs também pode oferecer suporte *sessões*. Uma sessão (e a implementação de <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> do tipo <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) correlaciona todas as mensagens enviadas e recebidas em um canal. O padrão de solicitação-resposta é uma sessão de duas mensagens independente, como a solicitação e resposta são correlacionadas. Em contraste, o padrão de solicitação-resposta que oferece suporte a sessões implica que todos os pares de solicitação/resposta naquele canal são correlacionados com o outro. Isso lhe dá um total de seis MEPs à sua escolha:  
  
-   Datagrama  
  
-   Solicitação-resposta  
  
-   Duplex  
  
-   Datagrama com sessões  
  
-   Solicitação-resposta com sessões  
  
-   Duplex com sessões  
  
> [!NOTE]
>  Para o transporte UDP, a MEPS somente com suporte é datagrama, porque UDP é inerentemente um incêndio e esquecer de protocolo.  
  
## <a name="sessions-and-sessionful-channels"></a>Sessões e canais de sessão  
 No mundo de rede, há protocolos orientados a conexão (por exemplo, TCP) e protocolos de conexão menor (por exemplo, UDP). WCF usa a sessão de termo significa uma abstração de lógica de conexão semelhante. Protocolos WCF de sessão são semelhantes aos protocolos de rede orientados a conexão e protocolos WCF sem sessão são semelhantes aos protocolos de rede de conexão sem.  
  
 No modelo de objeto do canal, cada sessão lógica manifesta como uma instância de um canal de sessão. Portanto, cada nova sessão criada pelo cliente e aceitos no serviço, corresponde a um novo canal de sessão em cada lado. A diagrama a seguir mostra, na parte superior, a estrutura de canais sem sessão e, na parte inferior, a estrutura de canais de sessão.  
  
 ![Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Um cliente cria um novo canal de sessão e envia uma mensagem. No lado do serviço, a escuta de canal recebe essa mensagem e detecta que ele pertence a uma nova sessão para que ele cria um novo canal de sessão e entrega-o para o aplicativo (em resposta ao aplicativo de chamada AcceptChannel no ouvinte de canal). Em seguida, o aplicativo recebe essa mensagem e todas as mensagens subsequentes, enviadas na mesma sessão por meio do mesmo canal de sessão.  
  
 Outro cliente (ou o mesmo cliente) cria uma nova sessão e envia uma mensagem. O ouvinte de canal detecta essa mensagem está em uma nova sessão e cria um novo canal de sessão e o processo se repete.  
  
 Sem sessões, não há nenhuma correlação entre canais e sessões. Portanto, um ouvinte de canal cria apenas um canal por meio do qual todas as mensagens recebidas são entregues ao aplicativo. Também não há nenhuma mensagem de ordenação porque não há nenhuma sessão na qual manter a ordem das mensagens. A parte superior do gráfico anterior ilustra uma troca de mensagens sem sessão.  
  
## <a name="starting-and-terminating-sessions"></a>Iniciar e encerrar sessões  
 Sessões são iniciadas no cliente, simplesmente criando um novo canal de sessão. Eles são iniciados no serviço quando o serviço recebe uma mensagem que foi enviada em uma nova sessão. Da mesma forma, as sessões são finalizadas pelo fechamento ou anulação de um canal de sessão.  
  
 A exceção a isso é <xref:System.ServiceModel.Channels.IDuplexSessionChannel> que é usado para enviar e receber mensagens em um padrão de sessão de comunicação duplex. É possível que um lado queira parar de enviar mensagens, mas continuar a receber mensagens, portanto, ao usar <xref:System.ServiceModel.Channels.IDuplexSessionChannel> há um mecanismo que permite que você feche a sessão de saída indicando não enviará mais mensagens, mas manter a sessão de entrada aberto permitindo que você continue a receber mensagens.  
  
 Em geral, as sessões são fechadas no lado de saída e não no lado de entrada. Ou seja, canais de sessão de saída podem ser fechados, assim corretamente encerrar a sessão. Fechar um canal de sessão de saída faz com que o canal de entrada sessão correspondente retornar nulo para a aplicativo que chama <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> sobre o <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 No entanto sessão canais de entrada devem ser fechados não, a menos que <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> no <xref:System.ServiceModel.Channels.IDuplexSessionChannel> retorna null, indicando que a sessão já está fechada. Se <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> no <xref:System.ServiceModel.Channels.IDuplexSessionChannel> tem não retornou um valor nulo, fechar um canal de sessão de entrada pode gerar uma exceção porque ele poderá receber mensagens inesperadas durante o fechamento. Se um receptor deseja encerrar uma sessão antes do remetente, ele deve chamar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> no canal de entrada, que encerra a sessão abruptamente.  
  
## <a name="writing-sessionful-channels"></a>Canais de sessão de gravação  
 Como criar um canal de sessão, há algumas coisas que seu canal deve fazer para fornecer sessões. No lado de envio, o canal precisa:  
  
-   Para cada novo canal, crie uma nova sessão e associá-lo a uma nova id de sessão que é uma cadeia de caracteres exclusiva. Ou obtenha uma nova sessão do canal sessão abaixo na pilha.  
  
-   Para cada mensagem enviada usando esse canal, se o seu canal criou a sessão (em vez de obtenção da camada abaixo), você precisa associar a mensagem com a sessão. Para canais de protocolo, normalmente isso é feito pela adição de um cabeçalho SOAP. Para canais de transporte, normalmente isso é feito criando uma nova conexão de transporte ou adicionando informações de sessão para o protocolo de enquadramento.  
  
-   Para cada mensagem enviada usando esse canal, você precisa fornecer as garantias de entrega mencionadas acima. Se você depender do canal abaixo você para fornecer a sessão, esse canal também fornecerá as garantias de entrega. Se você está fornecendo a sessão, você precisa implementar essas garantias como parte do seu protocolo. Em geral, se você estiver escrevendo um canal de protocolo que assume o WCF em ambos os lados podem exigir o transporte TCP ou o canal de mensagens confiáveis e dependem de um para fornecer uma sessão.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> é chamado em seu canal, execute o trabalho necessário para fechar a sessão usando o tempo limite especificado ou o padrão. Isso pode ser tão simple quanto chamar <xref:System.ServiceModel.ICommunicationObject.Close%2A> no canal abaixo (se você obteve apenas a sessão dele) ou enviar uma mensagem SOAP especial ou fechar uma conexão de transporte.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> é chamado em seu canal, encerra a sessão abruptamente sem executar e/s. Isso pode significar fazer nada ou pode envolver a anulação de uma conexão de rede ou algum outro recurso.  
  
 No lado de recebimento, o canal precisa:  
  
-   Para cada mensagem de entrada, o ouvinte do canal deve detectar a sessão que pertence a. Se esta for a primeira mensagem na sessão, o ouvinte do canal deve criar um novo canal e retorná-lo da chamada para <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. Caso contrário, o ouvinte do canal deve localizar o canal existente que corresponde à sessão e entrega a mensagem por meio do canal.  
  
-   Se o canal está fornecendo a sessão (junto com as garantias de entrega necessária) lado de recebimento pode ser necessária para executar algumas ações, como mensagens reordenar ou enviar confirmações.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Close%2A> é chamado em seu canal, execute o trabalho necessário para fechar a sessão, o tempo limite especificado ou o padrão. Isso pode resultar em exceções se o canal recebe uma mensagem ao aguardar o tempo limite de fechamento expirar. Isso ocorre porque o canal será no estado de fechamento quando ele recebe uma mensagem para que ela lançaria.  
  
-   Quando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> é chamado em seu canal, encerra a sessão abruptamente sem executar e/s. Novamente, isso pode significar fazer nada ou pode envolver a anulação de uma conexão de rede ou algum outro recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md)
