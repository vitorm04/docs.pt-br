---
title: Atividades de mensagem
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 1e65a3ead9df4103fb270911e3bbb2cc03fcfcba
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347571"
---
# <a name="messaging-activities"></a>Atividades de mensagem

As atividades de mensagens permitem que os fluxos de trabalho enviem e recebam mensagens do WCF. Ao adicionar atividades de mensagens a um fluxo de trabalho, você pode modelar quaisquer MEP (padrões de troca de mensagens) arbitrariamente complexos.

## <a name="message-exchange-patterns"></a>Padrões de troca de mensagens

Há três padrões básicos de troca de mensagens:

- **Datagrama** -ao usar o datagrama MEP o cliente envia uma mensagem para o serviço, mas o serviço não responde. Isso às vezes é chamado de "incêndio e esquecido". Um incêndio e esquecido o Exchange é um que requer a confirmação fora de banda da entrega bem-sucedida. A mensagem pode ser perdida em trânsito e nunca alcançar o serviço. Se o cliente enviar uma mensagem com êxito, ele não garante que o serviço tenha recebido a mensagem. O datagrama é um bloco de construção fundamental para mensagens, pois você pode criar seu próprio MEPs sobre ele.

- **Solicitação-resposta** -ao usar o MEP de solicitação-resposta o cliente envia uma mensagem para o serviço, o serviço faz o processamento necessário e, em seguida, envia uma resposta de volta ao cliente. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são RPC (chamadas de procedimento remoto) e solicitações GET de navegador. Esse padrão também é conhecido como Half-duplex.

- **Duplex** – ao usar o duplex MEP, o cliente e o serviço podem enviar mensagens entre si em qualquer ordem. O duplex MEP é como uma conversa telefônica, onde cada palavra que está sendo falada é uma mensagem.

As atividades de mensagens permitem que você implemente qualquer um desses MEPs básicos, bem como qualquer MEP arbitrariamente complexa.

## <a name="messaging-activities"></a>Atividades de mensagem

O [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] define as seguintes atividades de mensagens:

- <xref:System.ServiceModel.Activities.Send>-use a atividade <xref:System.ServiceModel.Activities.Send> para enviar uma mensagem.

- <xref:System.ServiceModel.Activities.SendReply>-use a atividade <xref:System.ServiceModel.Activities.SendReply> para enviar uma resposta a uma mensagem recebida. Essa atividade é usada pelos serviços de fluxo de trabalho ao implementar um MEP de solicitação/resposta.

- <xref:System.ServiceModel.Activities.Receive>-use a atividade <xref:System.ServiceModel.Activities.Receive> para receber uma mensagem.

- <xref:System.ServiceModel.Activities.ReceiveReply>-use a atividade <xref:System.ServiceModel.Activities.ReceiveReply> para receber uma mensagem de resposta. Essa atividade é usada por clientes de serviço de fluxo de trabalho ao implementar um MEP de solicitação/resposta.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Atividades de mensagens e padrões de troca de mensagens

Um dataMEP de datagrama envolve um cliente que envia uma mensagem e um serviço que recebe a mensagem. Se o cliente for um fluxo de trabalho, use uma atividade de <xref:System.ServiceModel.Activities.Send> para enviar a mensagem. Para receber essa mensagem em um fluxo de trabalho, use uma atividade de <xref:System.ServiceModel.Activities.Receive>. As atividades <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> têm uma propriedade denominada `Content`. Essa propriedade contém os dados que estão sendo enviados ou recebidos. Ao implementar a solicitação-Response MEP, o cliente e o serviço usam pares de atividades. O cliente usa uma atividade de <xref:System.ServiceModel.Activities.Send> para enviar a mensagem e uma atividade de <xref:System.ServiceModel.Activities.ReceiveReply> para receber a resposta do serviço. Essas duas atividades são associadas entre si pela propriedade <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>. Essa propriedade é definida para a atividade de <xref:System.ServiceModel.Activities.Send> que enviou a mensagem original. O serviço também usa um par de atividades associadas: <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>. Essas duas atividades são associadas pela propriedade <xref:System.ServiceModel.Activities.SendReply.Request%2A>. Essa propriedade é definida para a atividade de <xref:System.ServiceModel.Activities.Receive> que recebeu a mensagem original. As atividades <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply>, como <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> permitem enviar uma instância de <xref:System.ServiceModel.Channels.Message> ou um tipo de contrato de mensagem.

Devido à natureza de execução demorada dos fluxos de trabalho, é importante que o padrão duplex de comunicação também dê suporte a conversas de longa execução. Para dar suporte a conversas de execução longa, os clientes que iniciam a conversa devem fornecer ao serviço uma oportunidade para chamá-lo novamente mais tarde, quando os dados estiverem disponíveis. Por exemplo, uma solicitação de ordem de compra é enviada para aprovação do gerente, mas pode não ser processada por um dia, uma semana ou até mesmo um ano; o fluxo de trabalho que gerencia a aprovação da ordem de compra deve saber retomar depois que a aprovação é fornecida. Há suporte para esse padrão de comunicação duplex em fluxos de trabalho usando a correlação. Para implementar um padrão duplex, use <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> atividades. Na <xref:System.ServiceModel.Activities.Receive> atividade, inicialize uma correlação usando <xref:System.ServiceModel.Activities.CorrelationHandle>. Na <xref:System.ServiceModel.Activities.Send> atividade, defina o identificador de correlação como o valor da propriedade <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>. Para obter mais informações, consulte [duplex durável](durable-duplex-correlation.md).

> [!NOTE]
> A implementação de duplex do fluxo de trabalho usando uma correlação de retorno de chamada ("duplex durável") destina-se a conversas de longa execução. Isso não é o mesmo que o WCF duplex com contratos de retorno de chamada em que a conversa é de execução curta (o tempo de vida do canal).

## <a name="message-formatting-and-messaging-activities"></a>Formatação de mensagens e atividades de mensagens

As atividades <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.ReceiveReply> têm uma propriedade denominada `Content`. Essa propriedade é do tipo <xref:System.ServiceModel.Activities.ReceiveContent> e representa os dados que o <xref:System.ServiceModel.Activities.Receive> ou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> recebe. O .NET Framework define duas classes relacionadas chamadas <xref:System.ServiceModel.Activities.ReceiveMessageContent> e <xref:System.ServiceModel.Activities.ReceiveParametersContent> ambas derivam de <xref:System.ServiceModel.Activities.ReceiveContent>. Defina a propriedade `Content` da atividade de <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.ReceiveReply> como uma instância de um desses tipos para receber dados em um serviço de fluxo de trabalho. O tipo a ser usado depende do tipo de dados que a atividade recebe. Se a atividade receber um objeto `Message` ou um tipo de contrato de mensagem, use <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Se a atividade receber um conjunto de contratos de dados ou tipos XML que podem ser serializados, use <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> permite que você envie vários parâmetros, enquanto <xref:System.ServiceModel.Activities.ReceiveMessageContent> só permite enviar um objeto, a mensagem (ou o tipo de contrato de mensagem).

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent> também pode ser usado com um único contrato de dados ou tipo XML que pode ser serializado. A diferença entre usar <xref:System.ServiceModel.Activities.ReceiveParametersContent> com um único parâmetro e o objeto passado diretamente para <xref:System.ServiceModel.Activities.ReceiveMessageContent> é o formato de fio. O conteúdo do parâmetro é encapsulado em um elemento XML que corresponde ao nome da operação e o objeto serializado é encapsulado em um elemento XML usando o nome do parâmetro (por exemplo, `<Echo><msg>Hello, World</msg></Echo>`). O conteúdo da mensagem não é encapsulado pelo nome da operação. Em vez disso, o objeto serializado é colocado dentro de um elemento XML usando o nome de tipo qualificado por XML (por exemplo, `<string>Hello, World</string>`).

As atividades <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.SendReply> também têm uma propriedade chamada `Content`. Essa propriedade é do tipo <xref:System.ServiceModel.Activities.SendContent> e representa os dados que o <xref:System.ServiceModel.Activities.Send> ou a atividade de <xref:System.ServiceModel.Activities.SendReply> envia. O .NET Framework define dois tipos relacionados chamados <xref:System.ServiceModel.Activities.SendMessageContent> e <xref:System.ServiceModel.Activities.SendParametersContent> ambos derivam de <xref:System.ServiceModel.Activities.SendContent>. Defina a propriedade `Content` da atividade de <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply> como uma instância de um desses tipos para enviar dados de um serviço de fluxo de trabalho. O tipo a ser usado depende do tipo de dados que a atividade envia. Se a atividade enviar um objeto `Message` ou um tipo de contrato de mensagem, use <xref:System.ServiceModel.Activities.SendMessageContent>. Se a atividade enviar um tipo de contrato de dados, use <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> permite que você envie vários parâmetros, enquanto <xref:System.ServiceModel.Activities.SendMessageContent> só permite enviar um objeto, a mensagem (ou o tipo de contrato de mensagem).

Ao programar imperativamente com as atividades de mensagens, você usa o <xref:System.Activities.InArgument%601> genérico e <xref:System.Activities.OutArgument%601> para encapsular os objetos atribuídos às propriedades da mensagem ou dos parâmetros das atividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.ReceiveReply>. Use <xref:System.Activities.InArgument%601> para as atividades <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.SendReply> e <xref:System.Activities.OutArgument%601> para atividades <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.ReceiveReply>. `In` argumentos são usados com as atividades Send porque os dados estão sendo passados para as atividades. `Out` argumentos são usados com as atividades Receive porque os dados estão sendo passados das atividades, conforme mostrado no exemplo a seguir.

```csharp
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

Ao implementar um serviço de fluxo de trabalho que define uma operação de solicitação/resposta que retorna void, você deve instanciar uma atividade de <xref:System.ServiceModel.Activities.SendReply> e definir a propriedade <xref:System.ServiceModel.Activities.SendReply.Content%2A> como uma instância vazia de um dos tipos de conteúdo (<xref:System.ServiceModel.Activities.SendMessageContent> ou <xref:System.ServiceModel.Activities.SendParametersContent>), conforme mostrado no exemplo a seguir.

```csharp
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

## <a name="add-service-reference"></a>Adicionar referência de serviço

Ao chamar um serviço de fluxo de trabalho de um aplicativo de fluxo de trabalho, o Visual Studio 2012 gera atividades de mensagens personalizadas que encapsulam as <xref:System.ServiceModel.Activities.Send> usuais e <xref:System.ServiceModel.Activities.ReceiveReply> atividades usadas em um MEP de solicitação/resposta. Para usar esse recurso, clique com o botão direito do mouse no projeto cliente no Visual Studio e selecione **adicionar** > **referência de serviço**. Digite o endereço base do serviço na caixa endereço e clique em ir. Os serviços disponíveis são exibidos na caixa **Serviços:** . Expanda o nó de serviço para exibir os contratos com suporte. Selecione o contrato que você deseja chamar e a lista de operações disponíveis é exibida na caixa **operações** . Em seguida, você pode especificar o namespace para a atividade gerada e clicar em **OK**. Em seguida, você verá uma caixa de diálogo que diz que a operação foi concluída com êxito e que as atividades personalizadas geradas estão na caixa de ferramentas depois que você reconstruiu o projeto. Há uma atividade para cada operação definida no contrato de serviço. Depois de recriar o projeto, você pode arrastar e soltar as atividades personalizadas em seu fluxo de trabalho e definir todas as propriedades necessárias na janela Propriedades.

## <a name="messaging-activity-templates"></a>Modelos de atividade de mensagens

Para facilitar a configuração de um MEP de solicitação/resposta no cliente e no serviço, o Visual Studio 2012 fornece dois modelos de atividade de mensagens. `System.ServiceModel.Activities.Design.ReceiveAndSendReply` é usado no serviço e `System.ServiceModel.Activities.Design.SendAndReceiveReply` é usado no cliente. Em ambos os casos, os modelos adicionam as atividades de mensagens apropriadas ao seu fluxo de trabalho. No serviço, o `System.ServiceModel.Activities.Design.ReceiveAndSendReply` adiciona uma atividade de <xref:System.ServiceModel.Activities.Receive> seguida por uma atividade de <xref:System.ServiceModel.Activities.SendReply>. A propriedade <xref:System.ServiceModel.Activities.SendReply.Request> é definida automaticamente para a atividade de <xref:System.ServiceModel.Activities.Receive>. No cliente, o `System.ServiceModel.Activities.Design.SendAndReceiveReply` adiciona uma atividade de <xref:System.ServiceModel.Activities.Send> seguida por uma <xref:System.ServiceModel.Activities.ReceiveReply>. A propriedade <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> é definida automaticamente para a atividade de <xref:System.ServiceModel.Activities.Send>. Para usar esses modelos, basta arrastar e soltar o modelo apropriado no fluxo de trabalho.

## <a name="messaging-activities-and-transactions"></a>Atividades e transações de mensagens

Quando uma chamada é feita a um serviço de fluxo de trabalho, você pode querer fluir uma transação para a operação de serviço. Para fazer isso, coloque a atividade de <xref:System.ServiceModel.Activities.Receive> em uma atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope>. A atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> contém uma atividade de `Receive` e um corpo. A transação flui para o serviço permanece em ambiente durante a execução do corpo do <xref:System.ServiceModel.Activities.TransactedReceiveScope>. A transação é concluída quando o corpo termina de ser executado. Para obter mais informações sobre fluxos de trabalho e transações, consulte [Transações de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Veja também

- [Como enviar e receber falhas nos serviços de fluxo de trabalho](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Criando um serviço de fluxo de trabalho de longa execução](creating-a-long-running-workflow-service.md)
