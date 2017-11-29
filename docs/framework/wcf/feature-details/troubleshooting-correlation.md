---
title: "Correlação de solução de problemas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07fd03d929c99638b2cb148beded118bbdd679a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-correlation"></a>Correlação de solução de problemas
Correlação é usada para relacionar as mensagens do serviço de fluxo de trabalho entre si e com a instância de fluxo de trabalho correto, mas se ele não está configurado corretamente, as mensagens não serão recebidas e aplicativos não funcionarão corretamente. Este tópico fornece uma visão geral dos vários métodos para solução de problemas de correlação e também lista alguns problemas comuns que podem ocorrer quando você usar a correlação.  
  
## <a name="handle-the-unknownmessagereceived-event"></a>Manipular o evento UnknownMessageReceived  
 O <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> evento ocorre quando uma mensagem desconhecida é recebida por um serviço, inclusive as mensagens que não podem ser correlacionadas a uma instância existente. Para serviços de hospedagem interna, este evento pode ser tratado no aplicativo host.  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 Para serviços hospedados na Web, esse evento pode ser tratado derivando uma classe de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> e substituindo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.  
  
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
  
 Este arquivo <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> , em seguida, pode ser especificado no `svc` arquivo para o serviço.  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 Quando esse manipulador é chamado, a mensagem pode ser recuperada usando o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> propriedade o <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>e será parecida com a seguinte mensagem.  
  
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
  
 Inspecionar mensagens enviadas para o <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> manipulador possam fornecer pistas sobre por que a mensagem não correlacionar a uma instância do serviço de fluxo de trabalho.  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Usar o rastreamento para monitorar o andamento do fluxo de trabalho  
 Controle fornece uma maneira de monitorar o progresso de um fluxo de trabalho. Por padrão, os registros de rastreamento são emitidos para eventos de ciclo de vida do fluxo de trabalho, eventos de ciclo de vida da atividade, a propagação de falhas e retomada de indicador. Além disso, os registros de rastreamento personalizadas podem ser emitidos por atividades personalizadas. Ao solucionar problemas de correlação, a atividade de controle de registros, o indicador retomada e os registros de propagação de falha são mais úteis. A atividade de registros de controle pode ser usada para determinar o progresso atual do fluxo de trabalho e pode ajudar a identificar quais mensagens atividade está aguardando para mensagens. Registros de retomada de indicador são úteis porque elas indicam que uma mensagem foi recebida pelo fluxo de trabalho e os registros de propagação de falhas fornecem um registro de qualquer falha no fluxo de trabalho. Para habilitar o rastreamento, especifique os detalhes desejados <xref:System.Activities.Tracking.TrackingParticipant> no <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> do <xref:System.ServiceModel.Activities.WorkflowServiceHost>. No exemplo a seguir, o `ConsoleTrackingParticipant` (da [controle personalizado](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) exemplo) é configurada usando o controle de perfil padrão.  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Um participante de rastreamento como o ConsoleTrackingParticipant é útil para serviços de hospedagem interna de fluxo de trabalho que têm uma janela do console. Para um serviço hospedado na Web, um participante de rastreamento que registra as informações de rastreamento em um armazenamento durável deve ser usado, como o interno <xref:System.Activities.Tracking.EtwTrackingParticipant>, ou um participante de acompanhamento personalizado que registra as informações em um arquivo, como o `TextWriterTrackingParticpant` do [ Usando um arquivo de texto de controle](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) exemplo.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]controle e configurando o controle para um serviço de fluxo de trabalho hospedado na Web, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [configurar rastreamento para um fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)e o [controle &#91; Exemplos de WF &#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) exemplos.  
  
## <a name="use-wcf-tracing"></a>Usar o rastreamento do WCF  
 Rastreamento de WCF fornece o rastreamento do fluxo de mensagens para e de um serviço de fluxo de trabalho. Essas informações de rastreamento são útil ao solucionar problemas de correlação, especialmente para correlação baseada em conteúdo. Para habilitar o rastreamento, especifique os ouvintes de rastreamento desejado no `system.diagnostics` seção o `web.config` arquivo se o serviço de fluxo de trabalho estiver hospedado na Web, ou o `app.config` arquivo caso o serviço de fluxo de trabalho é hospedado automaticamente. Para incluir o conteúdo das mensagens de erro no arquivo de rastreamento, especifique `true` para `logEntireMessage` no `messageLogging` elemento o `diagnostics` seção `system.serviceModel`. No exemplo a seguir, as informações de rastreamento, incluindo o conteúdo das mensagens, estão configuradas para ser gravado em um arquivo chamado `service.svclog`.  
  
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
  
 Para exibir as informações de rastreamento que estão contidas no `service.svclog`, o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) é usado. Isso é especialmente útil quando correlação baseada em conteúdo de solução de problemas problemas porque você pode exibir o conteúdo da mensagem e veja exatamente o que está sendo passado, e se ele corresponde a <xref:System.ServiceModel.CorrelationQuery> para a correlação baseada em conteúdo. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WCF de rastreamento, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="common-context-exchange-correlation-issues"></a>Problemas comuns de correlação de troca de contexto  
 Certos tipos de correlação exigem que um tipo específico de associação é usado para a correlação funcione corretamente. Os exemplos incluem a correlação de solicitação-resposta, o que exige uma associação bidirecional como <xref:System.ServiceModel.BasicHttpBinding>e a correlação de intercâmbio de contexto, o que exige um baseado no contexto de associação, como <xref:System.ServiceModel.BasicHttpContextBinding>. A maioria das ligações oferece suporte a operações bidirecionais para que isso não é um problema comum para a correlação de solicitação-resposta, mas há apenas uma série de associações com base em contexto incluindo <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, e <xref:System.ServiceModel.NetTcpContextBinding>. Se um essas associações não é usado, a chamada inicial para um serviço de fluxo de trabalho será bem-sucedida, mas as chamadas subsequentes falhará com o seguinte <xref:System.ServiceModel.FaultException>.  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 As informações de contexto que são usadas para a correlação de contexto podem ser retornadas pelo <xref:System.ServiceModel.Activities.SendReply> para o <xref:System.ServiceModel.Activities.Receive> atividade que inicializa a correlação de contexto quando usando uma operação bidirecional, ou pode ser especificado pelo chamador se a operação unidirecional. Se o contexto não é enviado pelo chamador ou retornado, o serviço de fluxo de trabalho e o mesmo <xref:System.ServiceModel.FaultException> descritas anteriormente serão retornados quando uma operação subsequente é invocada.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Intercâmbio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
## <a name="common-request-reply-correlation-issues"></a>Problemas comuns de correlação de solicitação-resposta  
 Correlação de solicitação-resposta é usada com um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par para implementar uma operação bidirecional em um serviço de fluxo de trabalho e com um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par que invoca uma operação bidirecional em outra Web serviço. Ao invocar uma operação bidirecional em um serviço WCF, o serviço pode ser uma imperativa tradicional baseada em código [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço ou pode ser um serviço de fluxo de trabalho. Para usar uma associação bidirecional forem usada, como de correlação de solicitação-resposta <xref:System.ServiceModel.BasicHttpBinding>, e as operações devem ser bidirecionais.  
  
 Se o serviço de fluxo de trabalho tem bidirecionais operações em paralelo ou sobreposição <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ou <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pares e a correlação implícita lidar com gerenciamento fornecido pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>pode não ser suficiente, principalmente em cenários de alto estresse, e as mensagens não podem ser roteadas corretamente. Para evitar que esse problema ocorra, é recomendável sempre especificar explicitamente um <xref:System.ServiceModel.Activities.CorrelationHandle> ao usar a correlação de solicitação-resposta. Ao usar o **SendAndReceiveReply** e **ReceiveAndSendReply** modelos da seção de mensagens do **caixa de ferramentas** no designer de fluxo de trabalho, um <xref:System.ServiceModel.Activities.CorrelationHandle> é explicitamente configurado por padrão. Ao criar um fluxo de trabalho por meio de código, o <xref:System.ServiceModel.Activities.CorrelationHandle> é especificado no <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> da primeira atividade do par. No exemplo a seguir, uma <xref:System.ServiceModel.Activities.Receive> atividade está configurada com uma explícita <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> especificado no <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.  
  
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
  
 Persistência não é permitida entre um <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> par ou um <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> par. É criada uma zona no-persist dura até concluíram as duas atividades. Se uma atividade, como uma atividade de atraso é desta zona no-persist e faz com que o fluxo de trabalho ficar ocioso, o fluxo de trabalho não será mantido até mesmo se o host está configurada para manter os fluxos de trabalho quando eles se tornam ociosos. Se uma atividade, como uma atividade persist, tenta manter explicitamente na zona não persistente, uma exceção fatal for lançada, anula o fluxo de trabalho e um <xref:System.ServiceModel.FaultException> é retornado ao chamador. Mensagem de exceção fatal "System. InvalidOperationException: Manter atividades não podem ser contidas em blocos sem persistência.". Essa exceção não é retornada ao chamador, mas pode ser observada se o rastreamento está habilitado. A mensagem para o <xref:System.ServiceModel.FaultException> retornado ao chamador é "a operação não foi executada porque WorkflowInstance '5836145b 7da2 - 49 d 0-a052-a49162adeab6' foi concluída".  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]correlação de solicitação-resposta, consulte [solicitação-resposta](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).  
  
## <a name="common-content-correlation-issues"></a>Problemas comuns de correlação de conteúdo  
 Correlação baseada em conteúdo é usada quando um serviço de fluxo de trabalho recebe várias mensagens e uma parte dos dados nas mensagens trocadas identifica a instância desejada. Correlação baseada em conteúdo usa esses dados na mensagem, como um número ou a ordem de ID de cliente, para rotear mensagens para a instância de fluxo de trabalho correto. Esta seção descreve alguns problemas comuns que podem ocorrer ao usar a correlação baseada em conteúdo.  
  
### <a name="ensure-the-identifying-data-is-unique"></a>Certifique-se de que os dados de identificação são exclusivos  
 Os dados que são usados para identificar a instância são transformados em uma chave de correlação. Deve-se ter cuidado para garantir que os dados que são usados para correlação são exclusivos ou então colisões na chave de hash podem ocorrer e gerar mensagens acabe sendo enviado. Por exemplo, uma correlação com base apenas em um nome de cliente pode causar um conflito porque pode haver vários clientes que têm o mesmo nome. Os dois-pontos (:) não devem ser usado como parte dos dados que são usados para correlacionar a mensagem porque ele já é usado para delimitar a consulta de mensagem chave e valor para formar a cadeia de caracteres que é transformado em hash posteriormente. Se estiver sendo usada a persistência, certifique-se de que os dados que identificam atuais não foi usados por uma instância previamente persistida. Desabilitar temporariamente persistência pode ajudar a identificar o problema. O rastreamento do WCF pode ser usado para exibir a chave de correlação calculada e é útil para depurar esse tipo de problema.  
  
### <a name="race-conditions"></a>Condições de corrida  
 Há um pequeno espaço no tempo entre o serviço de recebimento de uma mensagem e a correlação, na verdade, está sendo inicializado, durante o qual as mensagens de acompanhamento serão ignoradas. Se um serviço de fluxo de trabalho inicializa a correlação baseada em conteúdo usando dados passados do cliente em uma operação unidirecional, e o chamador envia mensagens de acompanhamento imediatas, essas mensagens serão ignoradas durante esse intervalo. Isso pode ser evitado usando-se uma operação bidirecional para inicializar a correlação, ou usando um <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
### <a name="correlation-query-issues"></a>Problemas de correlação de consulta  
 Consultas de correlação são usadas para especificar quais dados em uma mensagem são usados para correlacionar a mensagem. Esses dados são especificados usando uma consulta XPath. Se as mensagens para um serviço não estão sendo despachadas, embora tudo parece estar correta, uma estratégia para solução de problemas é para especificar um valor literal que corresponde ao valor dos dados de mensagem em vez de uma consulta XPath. Para especificar um valor literal, use o `string` função. No exemplo a seguir, uma <xref:System.ServiceModel.MessageQuerySet> está configurado para usar um valor de literal `11445` para o `OrderId` e a consulta XPath é comentada.  
  
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
  
 Se uma consulta XPath é configurada incorretamente, de modo que nenhum dado de correlação é recuperado, uma falha será retornada com a seguinte mensagem: "uma consulta de correlação gerou um conjunto de resultados vazio. Verifique se as consultas para o ponto de extremidade de correlação estão definidas corretamente." Uma maneira rápida de solucionar esse problema é substituir a consulta XPath com um valor literal, conforme descrito na seção anterior. Esse problema pode ocorrer se você usar o construtor de consultas XPath no **adicionar inicializadores de correlação** ou **definição de CorrelatesOn** caixas de diálogo e o serviço de fluxo de trabalho usa contratos de mensagem. No exemplo a seguir, é definida uma classe de contrato de mensagem.  
  
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
  
 Essa consulta XPath estaria correta se a <xref:System.ServiceModel.Activities.Receive> atividade parâmetros usados para os dados, mas como ele está usando um contrato de mensagem é incorreto. A seguinte consulta XPath é a consulta XPath correta para recuperar o `CartId` do cabeçalho.  
  
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
  
 A exemplo a seguir mostra um <xref:System.ServiceModel.Activities.Receive> atividade configurada para um `AddItem` operação que usa o contrato de mensagem anterior para receber dados. A consulta XPath está configurada corretamente.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]correlação baseada em conteúdo, consulte [baseada em conteúdo](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) e [Calculadora correlacionada](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) exemplo.
