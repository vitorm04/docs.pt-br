---
title: Correlação de solução de problemas
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121886"
---
# <a name="troubleshooting-correlation"></a>Correlação de solução de problemas
Correlação é usada para relacionar mensagens do serviço de fluxo de trabalho entre si e com a instância de fluxo de trabalho correto, mas se ele não está configurado corretamente, as mensagens não serão recebidas e aplicativos não funcionarão corretamente. Este tópico fornece uma visão geral dos vários métodos para solução de problemas de correlação e também lista alguns problemas comuns que podem ocorrer quando você usa a correlação.

## <a name="handle-the-unknownmessagereceived-event"></a>Manipular o evento UnknownMessageReceived
 O <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> evento ocorre quando uma mensagem desconhecida é recebida por um serviço, incluindo as mensagens que não podem ser correlacionadas a uma instância existente. Para serviços de hospedagem interna, esse evento pode ser tratado no aplicativo host.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 Para serviços hospedados na Web, esse evento pode ser tratado por uma classe a partir <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> e substituindo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 Esse custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> , em seguida, pode ser especificado no `svc` arquivo para o serviço.

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 Quando esse manipulador é chamado, a mensagem pode ser recuperada usando o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> propriedade do <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>e será semelhante a seguinte mensagem de erro.

```Output
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 Inspecionando mensagens enviadas para o <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> manipulador pode fornecer pistas sobre por que a mensagem se correlaciona a uma instância do serviço de fluxo de trabalho.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Usar o rastreamento para monitorar o progresso do fluxo de trabalho
 Controle fornece uma maneira de monitorar o progresso de um fluxo de trabalho. Por padrão, os registros de rastreamento são emitidos para eventos de ciclo de vida de fluxo de trabalho, eventos de ciclo de vida de atividades, propagação de falha e retomada do indicador. Além disso, os registros personalizados de rastreamento podem ser emitidos por atividades personalizadas. Ao solucionar problemas de correlação, a atividade de acompanhamento de registros, os registros de retomada do indicador e os registros de propagação de falha são mais úteis. A atividade de registros de rastreamento pode ser usada para determinar o progresso atual do fluxo de trabalho e pode ajudar a identificar quais atividades de mensagem no momento está aguardando as mensagens. Registros de retomada de indicador são úteis porque eles indicam que uma mensagem foi recebida pelo fluxo de trabalho e os registros de propagação de falha fornecem um registro de quaisquer falhas no fluxo de trabalho. Para habilitar o acompanhamento, especifique os detalhes desejados <xref:System.Activities.Tracking.TrackingParticipant> no <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> da <xref:System.ServiceModel.Activities.WorkflowServiceHost>. No exemplo a seguir, o `ConsoleTrackingParticipant` (da [acompanhamento personalizado](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) exemplo) é configurada usando o perfil padrão de rastreamento.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Um participante de rastreamento, como o ConsoleTrackingParticipant é útil para serviços de fluxo de trabalho auto-hospedado que têm uma janela do console. Para um serviço hospedado na Web, um participante de rastreamento que registra as informações de rastreamento em um repositório durável deve ser usado, como a conta interna <xref:System.Activities.Tracking.EtwTrackingParticipant>, ou um participante de acompanhamento personalizado que registra as informações em um arquivo.

 Para obter mais informações sobre o acompanhamento e configurando o rastreamento para um serviço de fluxo de trabalho hospedados na Web, consulte [fluxo de trabalho, controle e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configurando o rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)e o [ Controle &#91;exemplos do WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) exemplos.

## <a name="use-wcf-tracing"></a>Use o rastreamento do WCF
 Rastreamento do WCF fornece o rastreamento de fluxo de mensagens para e de um serviço de fluxo de trabalho. Essas informações de rastreamento são útil ao solucionar problemas de correlação, especialmente para correlação conteudo base. Para habilitar o rastreamento, especifique os ouvintes de rastreamento desejado na `system.diagnostics` seção o `web.config` se o serviço de fluxo de trabalho estiver hospedado na Web, de arquivos ou o `app.config` arquivo se o serviço de fluxo de trabalho é auto-hospedado. Para incluir o conteúdo das mensagens no arquivo de rastreamento, especifique `true` para `logEntireMessage` na `messageLogging` elemento no `diagnostics` seção `system.serviceModel`. No exemplo a seguir, as informações de rastreamento, incluindo o conteúdo das mensagens, estão configuradas para ser gravado em um arquivo chamado `service.svclog`.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 Para exibir as informações de rastreamento que estão contidas em `service.svclog`, o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) é usado. Isso é especialmente útil ao solucionar problemas de correlação conteudo base problemas porque você pode exibir o conteúdo da mensagem e ver exatamente o que está sendo passado, e se ele corresponde ao <xref:System.ServiceModel.CorrelationQuery> para a correlação conteudo base. Para obter mais informações sobre rastreamento de WCF, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Problemas de correlação de troca de contexto comuns
 Determinados tipos de correlação exigem que um tipo específico de associação é usado para a correlação funcione corretamente. Os exemplos incluem a correlação de solicitação-resposta, o que exige uma vinculação bidirecional, como <xref:System.ServiceModel.BasicHttpBinding>e correlação de intercâmbio de contexto, que exige uma com base no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>. A maioria das ligações dar suporte a operações bidirecionais para que isso não é um problema comum para a correlação de solicitação-resposta, mas há apenas um punhado de associações de contexto base incluindo <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, e <xref:System.ServiceModel.NetTcpContextBinding>. Se uma dessas associações não é usada, a chamada inicial para um serviço de fluxo de trabalho terá êxito, mas as chamadas subsequentes falharão com o seguinte <xref:System.ServiceModel.FaultException>.

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 As informações de contexto que são usadas para correlação de contexto podem ser retornadas pela <xref:System.ServiceModel.Activities.SendReply> para o <xref:System.ServiceModel.Activities.Receive> atividade que inicializa a correlação de contexto quando usando uma operação bidirecional, ou ele pode ser especificado pelo chamador se a operação unidirecional. Se o contexto não é enviado pelo chamador ou retornado pelo serviço de fluxo de trabalho, em seguida, o mesmo <xref:System.ServiceModel.FaultException> descritas anteriormente serão retornados quando uma operação subsequente é invocada.

## <a name="common-request-reply-correlation-issues"></a>Problemas comuns de correlação de solicitação-resposta
 Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que chama uma operação bidirecional em outra Web serviço. Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser qualquer um tradicional imperativo serviço do WCF com base no código ou pode ser um serviço de fluxo de trabalho. Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>, e as operações devem ser bidirecionais.

 Se o serviço de fluxo de trabalho tiver bidirecionais operações em paralelo ou sobrepostos <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ou <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pares e, em seguida, a correlação implícita lidar com gerenciamento fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>pode não ser suficiente, especialmente em cenários de alto desgaste, e as mensagens não podem ser roteadas corretamente. Para evitar que esse problema ocorra, é recomendável que você sempre especifique explicitamente um <xref:System.ServiceModel.Activities.CorrelationHandle> ao usar a correlação de solicitação-resposta. Ao usar o **SendAndReceiveReply** e **ReceiveAndSendReply** modelos da seção de mensagens a **caixa de ferramentas** no designer de fluxo de trabalho, um <xref:System.ServiceModel.Activities.CorrelationHandle> é explicitamente configurado por padrão. Ao criar um fluxo de trabalho por meio de código, o <xref:System.ServiceModel.Activities.CorrelationHandle> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> da primeira atividade no par. No exemplo a seguir, uma <xref:System.ServiceModel.Activities.Receive> atividade está configurada com uma explícita <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> especificado no <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 Persistência não é permitida entre um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par ou uma <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par. Uma zona sem persistir é criada que dura até que ambas as atividades sejam concluídas. Se uma atividade, como uma atividade de atraso é nesta zona sem persistir e faz com que o fluxo de trabalho se torne ocioso, o fluxo de trabalho não persistirá mesmo que ele o host está configurado para persistir fluxos de trabalho quando eles se tornam ociosos. Se uma atividade, como uma atividade persist, tentar persistir explicitamente na zona sem persistir, uma exceção fatal é lançada, as anulações de fluxo de trabalho e um <xref:System.ServiceModel.FaultException> é retornado ao chamador. A mensagem de exceção fatal é "System. InvalidOperationException: Manter atividades não podem ser contidas dentro de blocos sem persistência.". Essa exceção não é retornada ao chamador, mas pode ser observada se o rastreamento está habilitado. A mensagem para o <xref:System.ServiceModel.FaultException> retornado ao chamador é "a operação pode não ser executada como WorkflowInstance '5836145b 7da2 - 49 d 0-a052-a49162adeab6' foi concluída".

 Para obter mais informações sobre a correlação de solicitação-resposta, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Problemas comuns de correlação de conteúdo
 Correlação conteudo base é usada quando um serviço de fluxo de trabalho recebe várias mensagens e uma parte dos dados em que as mensagens trocadas identifica a instância desejada. Correlação conteudo base que usa esses dados na mensagem, como um número ou a ordem de ID de cliente, para rotear mensagens para a instância de fluxo de trabalho correto. Esta seção descreve vários problemas comuns que podem ocorrer ao usar a correlação conteudo base.

### <a name="ensure-the-identifying-data-is-unique"></a>Verifique se que os dados de identificação são exclusivos
 Os dados que são usados para identificar a instância são transformados em uma chave de correlação. Deve-se ter cuidado para garantir que os dados que são usados para correlação são exclusivos ou então colisões na chave de hash podem ocorrer e causar mensagens acabe sendo enviado. Por exemplo, uma correlação com base somente em um nome de cliente pode causar uma colisão, porque pode haver vários clientes que têm o mesmo nome. Os dois-pontos (:) não devem ser usado como parte dos dados que são usados para correlacionar a mensagem porque ele já é usado para delimitar a chave e o valor para formar a cadeia de caracteres de hash, posteriormente, a consulta de mensagem. Se a persistência está sendo usada, certifique-se de que os dados que identificam atuais não foi usados por uma instância previamente persistida. Desabilitar temporariamente a persistência pode ajudar a identificar esse problema. Rastreamento de WCF pode ser usado para exibir a chave de correlação calculada e é útil para depurar esse tipo de problema.

### <a name="race-conditions"></a>Condições de corrida
 Há um pequeno espaço no tempo entre o serviço receber uma mensagem e a correlação, na verdade, que está sendo inicializado, durante o qual as mensagens de acompanhamento serão ignoradas. Se um serviço de fluxo de trabalho inicializa a correlação conteudo base usando os dados passados do cliente em uma operação unidirecional e o chamador envia mensagens de acompanhamento de imediatas, essas mensagens serão ignoradas durante esse intervalo. Isso pode ser evitado por meio de uma operação bidirecional para inicializar a correlação, ou usando um <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Problemas de correlação de consulta
 Consultas de correlação são usadas para especificar quais dados em uma mensagem são usados para correlacionar a mensagem. Esses dados são especificados usando uma consulta XPath. Se as mensagens para um serviço não estão sendo despachadas, mesmo que tudo parece estar correta, uma estratégia para solução de problemas é para especificar um valor literal que corresponde ao valor dos dados da mensagem, em vez de uma consulta XPath. Para especificar um valor literal, use o `string` função. No exemplo a seguir, uma <xref:System.ServiceModel.MessageQuerySet> está configurado para usar um valor literal `11445` para o `OrderId` e a consulta XPath é comentada.

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 Se uma consulta XPath está configurada incorretamente, de modo que nenhum dado de correlação é recuperado, uma falha será retornada com a seguinte mensagem: "uma consulta de correlação gerou um conjunto de resultados vazio. Verifique se as consultas de correlação para o ponto de extremidade estão configuradas corretamente." Uma maneira rápida de solucionar esse problema é substituir a consulta XPath com um valor literal, conforme descrito na seção anterior. Esse problema pode ocorrer se você usar o construtor de consultas XPath na **adicionar inicializadores de correlação** ou **definição de CorrelatesOn** caixas de diálogo e seu serviço de fluxo de trabalho usa contratos de mensagem. No exemplo a seguir, uma classe de contrato de mensagem é definida.

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 Este contrato de mensagem é usado por um <xref:System.ServiceModel.Activities.Receive> atividade em um fluxo de trabalho. O `CartId` no cabeçalho da mensagem é usada para correlacionar a mensagem para a instância correta. Se a consulta XPath que recupera o `CartId` é criado usando as caixas de diálogo correlação no designer de fluxo de trabalho, o XPath incorreto a seguir consulta é gerada.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Essa consulta XPath estaria correta se o <xref:System.ServiceModel.Activities.Receive> atividade os parâmetros usados para os dados, mas uma vez que ele está usando um contrato de mensagem é incorreto. A seguinte consulta XPath é a consulta XPath correta para recuperar o `CartId` do cabeçalho.

```
sm:header()/tempuri:CartId
```

Isso pode ser confirmado ao examinar o corpo da mensagem.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

A exemplo a seguir mostra uma <xref:System.ServiceModel.Activities.Receive> atividade configurada para um `AddItem` operação que usa o contrato de mensagem anterior para receber dados. A consulta XPath está configurada corretamente.

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
