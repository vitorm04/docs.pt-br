---
title: Atividades de mensagem
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 5ccace3ebea42957e1cc66602579d85cd8634435
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502707"
---
# <a name="messaging-activities"></a>Atividades de mensagem
As atividades de mensagem permitem que os fluxos de trabalho enviar e receber mensagens do WCF. Adicionando atividades de mensagem para um fluxo de trabalho, você pode modelar qualquer padrões de troca de mensagem arbitrariamente complexas (MEP).

## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem
 Há três padrões de troca de mensagens básicas:

-   **Datagrama** - ao usar o datagrama MEP o cliente envia uma mensagem para o serviço, mas o serviço não responde. Às vezes, isso é chamado "disparar e esquecer". A disparar e esquecer exchange é aquela que requer a confirmação de out-of-band de entrega bem-sucedida. A mensagem poderá ser perdida em trânsito e nunca alcançar o serviço. Se o cliente com êxito envia uma mensagem, ele não garante que o serviço recebeu a mensagem. O datagrama é um bloco de construção fundamental para mensagens, como você pode criar seus próprios MEPs sobre ele.

-   **Solicitação-resposta** - quando usando o MEP de solicitação-resposta o cliente envia uma mensagem para o serviço, o serviço faz o processamento necessário e, em seguida, envia uma resposta de volta para o cliente. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador GET solicitações. Esse padrão também é conhecido como half-duplex.

-   **Duplex** - quando usando o serviço e o cliente do MEP duplex pode enviar mensagens uns aos outros em qualquer ordem. O MEP duplex é como uma conversa de telefone, em que cada palavra que está sendo falada é uma mensagem.

 As atividades de mensagem permitem que você implemente, bem como qualquer um desses MEPs básicas qualquer MEP arbitrariamente complexo.

## <a name="messaging-activities"></a>Atividades de mensagem
 O [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] define as atividades de mensagem a seguir:

-   <xref:System.ServiceModel.Activities.Send>– Use o <xref:System.ServiceModel.Activities.Send> atividade para enviar uma mensagem.

-   <xref:System.ServiceModel.Activities.SendReply> – Use o <xref:System.ServiceModel.Activities.SendReply> atividade para enviar uma resposta a uma mensagem recebida. Essa atividade é usada pelos serviços de fluxo de trabalho ao implementar uma MEP de solicitação/resposta.

-   <xref:System.ServiceModel.Activities.Receive>– Use o <xref:System.ServiceModel.Activities.Receive> atividade para receber uma mensagem.

-   <xref:System.ServiceModel.Activities.ReceiveReply> – Use o <xref:System.ServiceModel.Activities.ReceiveReply> atividade para receber uma mensagem de resposta. Essa atividade é usada pelos clientes do serviço de fluxo de trabalho ao implementar uma MEP de solicitação/resposta.

## <a name="messaging-activities-and-message-exchange-patterns"></a>As atividades de mensagem e padrões de troca de mensagem
 Um datagrama MEP envolve um cliente que envia uma mensagem e um serviço de recebimento da mensagem. Se o cliente é um fluxo de trabalho, use um <xref:System.ServiceModel.Activities.Send> atividade para enviar a mensagem. Para receber essa mensagem em um fluxo de trabalho, use um <xref:System.ServiceModel.Activities.Receive> atividade. O <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> atividades cada têm uma propriedade chamada `Content`. Esta propriedade contém os dados que estão sendo enviados ou recebidos. Ao implementar o MEP de solicitação-resposta do cliente e o serviço usam pares de atividades. O cliente usa um <xref:System.ServiceModel.Activities.Send> atividade para enviar a mensagem e um <xref:System.ServiceModel.Activities.ReceiveReply> atividade para receber a resposta do serviço. Essas duas atividades são associadas entre si pelo <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> propriedade. Essa propriedade é definida como o <xref:System.ServiceModel.Activities.Send> atividade que enviou a mensagem original. O serviço também usa um par de atividades associadas: <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>. Essas duas atividades associadas pelo <xref:System.ServiceModel.Activities.SendReply.Request%2A> propriedade. Essa propriedade é definida como o <xref:System.ServiceModel.Activities.Receive> atividade que recebeu a mensagem original. O <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply> atividades, como <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> permitem que você envie um <xref:System.ServiceModel.Channels.Message> instância ou um tipo de contrato de mensagem.

 Devido à natureza de longa execução de fluxos de trabalho, é importante para que o duplex padrão de comunicação para também dar suporte a conversas de longa execução. Para dar suporte a conversas de longa execução, os clientes que iniciam a conversa devem fornecer o serviço a oportunidade de chamá-lo de volta em um momento posterior quando os dados se tornam disponíveis. Por exemplo, uma solicitação de pedido de compra é enviada para aprovação do gerente, mas não pode ser processada por dia, semana ou até mesmo um ano; o fluxo de trabalho que gerencia a aprovação de ordem de compra deve saber para retomar após a aprovação é fornecida. Esse padrão de comunicação duplex é compatível com fluxos de trabalho usando a correlação. Para implementar um padrão de duplex, use <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> atividades. Sobre o <xref:System.ServiceModel.Activities.Receive> atividade, inicialize uma correlação usando o valor da chave especial <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Sobre o <xref:System.ServiceModel.Activities.Send> atividade definida esse identificador de correlação como o <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> valor da propriedade. Para obter mais informações, consulte [Duplex durável](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).

> [!NOTE]
>  A implementação do fluxo de trabalho de duplex usando uma correlação de retorno de chamada ("verso durável") destina-se de conversas de longa execução. Isso não é o mesmo que o WCF duplex com contratos de retorno de chamada em que a conversa é curta execução (o tempo de vida do canal).

## <a name="message-formatting-and-messaging-activities"></a>Formatação de mensagem e atividades de mensagem
 O <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades têm uma propriedade chamada `Content`. Essa propriedade é do tipo <xref:System.ServiceModel.Activities.ReceiveContent> e representa os dados do <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.ReceiveReply> atividade receber. O .NET Framework define duas classes relacionadas chamadas <xref:System.ServiceModel.Activities.ReceiveMessageContent> e <xref:System.ServiceModel.Activities.ReceiveParametersContent> que são derivados de <xref:System.ServiceModel.Activities.ReceiveContent>. Defina as <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.ReceiveReply> da atividade `Content` propriedade a uma instância de um desses tipos para receber dados em um serviço de fluxo de trabalho. O tipo a ser usado depende do tipo de dados que recebe a atividade. Se a atividade recebe uma `Message` objeto ou uma mensagem de tipo de contrato, use <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Se a atividade recebe um conjunto de tipos XML que podem ser serializados ou contrato de dados, use <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> permite que você envie vários parâmetros, enquanto <xref:System.ServiceModel.Activities.ReceiveMessageContent> só permite que você enviar um objeto, a mensagem (ou tipo de contrato de mensagem).

> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> também pode ser usado com um contrato de dados único ou um tipo XML que pode ser serializado. A diferença entre usar <xref:System.ServiceModel.Activities.ReceiveParametersContent> com um único parâmetro e o objeto passado diretamente para <xref:System.ServiceModel.Activities.ReceiveMessageContent> é o formato de conexão. Conteúdo do parâmetro é encapsulado em um elemento XML que corresponde ao nome da operação e o objeto serializado é encapsulado em um elemento XML usando o nome do parâmetro (por exemplo, `<Echo><msg>Hello, World</msg></Echo>`). O conteúdo da mensagem não é encapsulado pelo nome da operação. Em vez disso, o objeto serializado é colocado dentro de um elemento XML usando o nome de tipo qualificado por XML (por exemplo, `<string>Hello, World</string>`).

 O <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.SendReply> atividades também têm uma propriedade chamada `Content`. Essa propriedade é do tipo <xref:System.ServiceModel.Activities.SendContent> e representa os dados do <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply> envios de atividade. O .NET Framework define dois tipos relacionados chamados <xref:System.ServiceModel.Activities.SendMessageContent> e <xref:System.ServiceModel.Activities.SendParametersContent> que são derivados de <xref:System.ServiceModel.Activities.SendContent>. Defina as <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply> da atividade `Content` propriedade para uma instância de um desses tipos para enviar dados de um serviço de fluxo de trabalho. O tipo a ser usado depende do tipo de dados que envia a atividade. Se a atividade enviar uma `Message` objeto ou uma mensagem de tipo de contrato, use <xref:System.ServiceModel.Activities.SendMessageContent>. Se a atividade enviar um uso de tipo de contrato de dados <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> permite que você envie vários parâmetros, enquanto <xref:System.ServiceModel.Activities.SendMessageContent> só permite que você envie um objeto, a mensagem (ou o tipo de contrato de mensagem).

 Ao programar em imperativa com as atividades de mensagens, você usar o genérico <xref:System.Activities.InArgument%601> e <xref:System.Activities.OutArgument%601> encapsulando os objetos que você atribui às propriedades da mensagem ou parâmetros de <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.ReceiveReply>atividades. Use <xref:System.Activities.InArgument%601> para o <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.SendReply> atividades e <xref:System.Activities.OutArgument%601> para <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades. `In` argumentos são usados com as atividades de envio, porque os dados que está sendo passados para as atividades. `Out` argumentos são usados com as atividades de recebimento, porque os dados estiverem sendo passados para atividades, conforme mostrado no exemplo a seguir.

```
Receive reserveSeat = new Receive
{
    ...
    Content = new ReceiveParametersContent
    {
        Parameters =
        {
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }
        }
    }
};
SendReply reserveSeat = new SendReply
{
    ...
    Request = reserveSeat,
    Content = new SendParametersContent
    {
        Parameters =
        {
            { "ReservationId", new InArgument<string>(reservationId) }
        }
    },
};
```

 Ao implementar um serviço de fluxo de trabalho que define uma operação de solicitação/resposta que retorna void, você deve criar uma instância de um <xref:System.ServiceModel.Activities.SendReply> atividade e conjunto de <xref:System.ServiceModel.Activities.SendReply.Content%2A> propriedade a uma instância vazia de um dos tipos de conteúdo (<xref:System.ServiceModel.Activities.SendMessageContent> ou <xref:System.ServiceModel.Activities.SendParametersContent>) conforme mostrado no exemplo a seguir.

```
Receive rcv = new Receive()
{
ServiceContractName = "IService",
OperationName = "NullReturningContract",
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )
};
SendReply sr = new SendReply()
{
Request = rcv
   Content = new SendParametersContent();
};
```

## <a name="add-service-reference"></a>Adicionar Referência de Serviço
 Ao chamar um serviço de fluxo de trabalho de um aplicativo de fluxo de trabalho [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] gera as atividades de mensagem personalizadas que encapsulam normais <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades usadas em uma MEP de solicitação/resposta. Para usar esse recurso, clique com botão direito no projeto cliente no Visual Studio e selecione **Add** > **referência de serviço**. Digite o endereço base do serviço na caixa de endereço e clique em Ir. Os serviços disponíveis são exibidos na **Services:** caixa. Expanda o nó de serviço para exibir os contratos de suporte. Selecione o contrato que você deseja chamar e a lista de operações disponíveis é exibida na **operações** caixa. Você pode, em seguida, especifique o namespace para a atividade gerada e clique em **Okey**. Você verá uma caixa de diálogo que diz que a operação foi concluída com êxito e que as atividades personalizados geradas estão na caixa de ferramentas depois que você tiver recriado o projeto. Há uma atividade para cada operação definida no contrato de serviço. Depois de recompilar o projeto de arrastar e soltar atividades personalizadas para seu fluxo de trabalho e defina as propriedades na janela Propriedades.

<!--## Messaging Activity Templates
 To make setting up a request/response MEP on the client and service easier, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.
-->
## <a name="messaging-activities-and-transactions"></a>Transações e as atividades de mensagem
 Quando é feita uma chamada para um serviço de fluxo de trabalho você talvez queira fluir uma transação para a operação de serviço. Para fazer esse lugar a <xref:System.ServiceModel.Activities.Receive> atividade dentro de um <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade. O <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade contém uma `Receive` atividade e um corpo. A transação fluída para o permanece serviço ambiente durante a execução do corpo do <xref:System.ServiceModel.Activities.TransactedReceiveScope>. A transação é concluída quando o corpo termina a execução. Para obter mais informações sobre fluxos de trabalho e transações, consulte [transações de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Consulte também
- [Como enviar e receber falhas nos serviços de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
