---
title: Extensibilidade de host de serviço do fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: eb35b9211bc55ee66f5bb5600ef86f40d4145191
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463999"
---
# <a name="workflow-service-host-extensibility"></a>Extensibilidade de host de serviço do fluxo de trabalho
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]fornece <xref:System.ServiceModel.Activities.WorkflowServiceHost> a classe para serviços de fluxo de trabalho de hospedagem. Essa classe é usada quando você está hospedando um serviço de fluxo de trabalho em um aplicativo gerenciado ou um serviço do Windows. Essa classe também é usada ao hospedar um serviço de fluxo de trabalho com o IIS (Internet Information Services, serviço de ativação de processos da Internet) ou o Serviço de Ativação de Processos do Windows (WAS). A <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe fornece pontos de extensão que permitem adicionar extensões personalizadas, alterar o comportamento ocioso e hospedar fluxos de trabalho não-serviço (fluxos de trabalho que não usam atividades de mensagens).  
  
## <a name="workflow-service-host-extensions"></a>Extensões do host do serviço de fluxo de trabalho  
 O <xref:System.ServiceModel.Activities.WorkflowServiceHost> contém <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> uma <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> propriedade do tipo que fornece <xref:System.ServiceModel.Activities.WorkflowServiceHost>métodos para adicionar extensões ao . Use <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> o método para adicionar uma extensão para cada instância de serviço do fluxo de trabalho. O delegado especificado é chamado para criar uma nova extensão quando uma instância de serviço de fluxo de trabalho é criada ou carregada a partir de um armazenamento de persistência. Use <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> o método para adicionar uma extensão para cada host de serviço de fluxo de trabalho, uma instância da extensão é compartilhada para todas as instâncias de serviço do fluxo de trabalho.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagir a exceções não manuseadas  
 O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> habilita-se a especificar a ação a ser tomada se uma exceção não tratada ocorrer dentro de um serviço de fluxo de trabalho. A <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> propriedade especifica um <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> dos valores:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– Aborta a instância de serviço do fluxo de trabalho.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Volta ao último estado persistiu e suspende a instância de serviço do fluxo de trabalho. Isso só ocorre se o fluxo de trabalho já tiver sido persistido pelo menos uma vez. Se não a instância do fluxo de trabalho for abortada.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Cancela a instância.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Encerra a instância.  
  
 Esse comportamento pode ser configurado em código, conforme mostrado no exemplo a seguir.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Ele também pode ser configurado em um arquivo de configuração, como mostrado no exemplo a seguir.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />
        </behavior>  
      </serviceBehaviors>  
</behaviors>
```  
  
## <a name="hosting-non-service-workflows"></a>Hospedagem de fluxos de trabalho sem serviço  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>podem ser usados para hospedar fluxos de trabalho não-serviço, ou fluxos de trabalho que não começam com uma <xref:System.ServiceModel.Activities.Receive> atividade ou fluxos de trabalho que não usam as atividades de mensagens. Os serviços de <xref:System.ServiceModel.Activities.Receive> fluxo de trabalho normalmente começam com uma atividade. Quando <xref:System.ServiceModel.Activities.WorkflowServiceHost> o recebe uma mensagem para um serviço de fluxo de trabalho, se ele ainda não estiver executando (ou persistir) uma nova instância de serviço de fluxo de trabalho é criada. Se um fluxo de trabalho não começar com uma atividade Receber, ele não pode ser iniciado enviando uma mensagem porque não há atividade para receber a mensagem. Para hospedar um fluxo de trabalho não-serviço, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>obtenha <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>uma classe <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> e substituição, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>e . Anular <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> se você quiser fornecer um ID de instância preferido. Substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> para criar um contexto de criação de fluxo <xref:System.ServiceModel.Activities.WorkflowCreationContext>de trabalho personalizado ou preencher uma instância do existente . Substituir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> para extrair manualmente o marcador da mensagem recebida. Se você substituir este método, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> você deve invocar em seu corpo de modo a responder à mensagem enviada ao WorkflowHostingEndpoint. Se você não fizer isso, um <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> limite pode eventualmente ser excedido. Em contratos bidirecionais, você pode ser capaz <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> de detectar sua falha de invocação devido à falha do cliente em receber uma resposta. Em contratos unidirecionais, você pode não reconhecer <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> o erro de não ligar <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> até que seja tarde demais, depois que o limite do acelerador for excedido. Para obter mais informações, consulte o Marcador de [currículo WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Para criar uma nova instância de um fluxo de trabalho não-serviço, declare um contrato de serviço que defina uma operação que cria uma nova instância. A operação de criação\<deve levar uma seqüência de string IDictionary, objeto> para passar quaisquer parâmetros de fluxo de trabalho necessários. Este contrato é implicitamente implementado pela <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>classe derivada. Ao hospedar o fluxo de trabalho, adicione uma instância <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>da <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> classe <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>derivada ao host ligando e chamando . Para criar uma instância do fluxo <xref:System.ServiceModel.ChannelFactory%601> de trabalho, crie <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>um tipo de contrato de serviço e chamada . Em seguida, você pode chamar a operação de criação definida em seu contrato de serviço.  
  
## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Atividades de mensagem](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
