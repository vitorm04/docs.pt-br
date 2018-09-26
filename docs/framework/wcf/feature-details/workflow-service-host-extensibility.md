---
title: Extensibilidade de host de serviço do fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 6541558601c8f5daf255f2e7e5d774e41b59be2d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171849"
---
# <a name="workflow-service-host-extensibility"></a>Extensibilidade de host de serviço do fluxo de trabalho
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fornece o <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe para hospedar os serviços de fluxo de trabalho. Essa classe é usada quando você esteja hospedando internamente um serviço de fluxo de trabalho em um aplicativo gerenciado ou um serviço do Windows. Essa classe também é usada ao hospedar um serviço de fluxo de trabalho com serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS). O <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe fornece pontos de extensão permitem adicionar extensões personalizadas, alterar o comportamento ocioso e hospedar fluxos de trabalho sem serviço (fluxos de trabalho que não usam as atividades de mensagem).  
  
## <a name="workflow-service-host-extensions"></a>Extensões de Host de serviço de fluxo de trabalho  
 O <xref:System.ServiceModel.Activities.WorkflowServiceHost> contém uma <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> propriedade do tipo <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> que fornece métodos para adicionar extensões para o <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Use o <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> método para adicionar uma extensão para cada instância de serviço de fluxo de trabalho. O delegado especificado é chamado para criar uma nova extensão quando uma instância de serviço de fluxo de trabalho é criada ou carregada de um repositório de persistência. Use o <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> método para adicionar uma extensão para cada host de serviço de fluxo de trabalho, uma instância da extensão é compartilhada por todas as instâncias de serviço de fluxo de trabalho.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagir a exceções sem tratamento  
 O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> permite que você especifique a ação a ser tomada se uma exceção sem tratamento ocorrer dentro de um serviço de fluxo de trabalho. O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> propriedade especifica o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> valores:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> – Anula a instância de serviço de fluxo de trabalho.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> – Reverte para o último estado persistente e suspende a instância do serviço de fluxo de trabalho. Isso ocorre apenas se o fluxo de trabalho já tiver sido persistido pelo menos uma vez. Se não for a instância de fluxo de trabalho é anulada.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> – Cancela a instância.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> – Encerra a instância.  
  
 Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Ele também pode ser configurado em um arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
```  
  
## <a name="hosting-non-service-workflows"></a>Hospedando fluxos de trabalho sem serviço  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> pode ser usado para hospedar fluxos de trabalho sem serviço ou fluxos de trabalho que o não começam com um <xref:System.ServiceModel.Activities.Receive> atividades ou fluxos de trabalho que não usam as atividades de mensagem. Serviços de fluxo de trabalho normalmente começam com um <xref:System.ServiceModel.Activities.Receive> atividade. Quando o <xref:System.ServiceModel.Activities.WorkflowServiceHost> recebe uma mensagem para um serviço de fluxo de trabalho, se ele não estiver sendo executado (ou persistentes) uma nova instância de serviço de fluxo de trabalho é criado. Se um fluxo de trabalho não começa com uma atividade de recebimento, ele não pode ser iniciado, enviando uma mensagem porque não há nenhuma atividade para receber a mensagem. Para hospedar um fluxo de trabalho sem serviço, derive uma classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> e substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, e <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> se você quiser fornecer uma ID de instância preferencial. Substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> para criar um contexto de criação de fluxo de trabalho personalizado ou preencher uma instância do existente <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> para extrair manualmente o indicador de mensagem de entrada. Se você substituir esse método, você deve chamar <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> em seu corpo para responder à mensagem enviada para o WorkflowHostingEndpoint. Se você não fizer isso, um <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limite pode ser eventualmente excedido. Em contratos bidirecionais, você poderá detectar sua falha para invocar <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> devido a falha do cliente para receber uma resposta. Em contratos unidirecionais, você pode não reconhecer o erro de falha ao chamar <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> até que seja muito tarde, após o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limite for excedido. Para obter mais informações, consulte o [WorkflowHostingEndpoint retomar indicador](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)para criar uma nova instância de fluxo de trabalho sem serviço, declare um contrato de serviço que define uma operação que cria uma nova instância. A operação de criação deve levar um IDictionary\<string, object > para passar por nenhuma necessários parâmetros de fluxo de trabalho. Implicitamente, esse contrato é implementado pelo <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-classe derivada. Ao hospedar o fluxo de trabalho, adicione uma instância das <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-classe derivada para o host chamando <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> e chame <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Para criar uma instância do fluxo de trabalho, crie uma <xref:System.ServiceModel.ChannelFactory%601> de seu tipo de contrato de serviço e chame <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Em seguida, você pode chamar a operação de criação definida no seu contrato de serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
