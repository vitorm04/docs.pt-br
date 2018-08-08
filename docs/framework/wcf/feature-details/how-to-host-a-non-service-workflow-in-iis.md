---
title: Como hospedar um fluxo de trabalho sem serviço no IIS
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496740"
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a><span data-ttu-id="91264-102">Como hospedar um fluxo de trabalho sem serviço no IIS</span><span class="sxs-lookup"><span data-stu-id="91264-102">How to: Host a non-service workflow in IIS</span></span>
<span data-ttu-id="91264-103">Fluxos de trabalho que não são serviços de fluxo de trabalho podem ser hospedados em IIS / WAS.</span><span class="sxs-lookup"><span data-stu-id="91264-103">Workflows that are not workflow services can be hosted under IIS/WAS.</span></span> <span data-ttu-id="91264-104">Isso é útil quando você precisa hospedar um fluxo de trabalho gravado por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="91264-104">This is useful when you need to host a workflow written by somebody else.</span></span> <span data-ttu-id="91264-105">Por exemplo, se o novo host do designer de fluxo de trabalho e permitir que os usuários criem seus próprios fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-105">For example, if you rehost the workflow designer and allow users to create their own workflows.</span></span>  <span data-ttu-id="91264-106">Hospedando fluxos de trabalho sem serviço no IIS fornece suporte para recursos como o desligamento ocioso, reciclagem de processo, o monitoramento de integridade do processo e a ativação baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="91264-106">Hosting non-service workflows in IIS provides support for features like process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="91264-107">Serviços de fluxo de trabalho hospedados no IIS contêm <xref:System.ServiceModel.Activities.Receive> atividades e o são ativados quando uma mensagem é recebida pelo IIS.</span><span class="sxs-lookup"><span data-stu-id="91264-107">Workflow services hosted in IIS contain <xref:System.ServiceModel.Activities.Receive> activities and are activated when a message is received by IIS.</span></span> <span data-ttu-id="91264-108">Fluxos de trabalho não não contêm atividades de mensagem e por padrão, não não possível ativar enviando uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="91264-108">Non-service workflows do not contain messaging activities, and by default cannot be activated by sending a message.</span></span>  <span data-ttu-id="91264-109">Você deve derivar uma classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> e definir um contrato de serviço que contém operações para criar uma instância do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-109">You must derive a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> and define a service contract that contains operations to create an instance of the workflow.</span></span> <span data-ttu-id="91264-110">Este tópico o orientará na criação de um fluxo de trabalho simple, definir um contrato de serviço que um cliente pode usar para ativar o fluxo de trabalho e derivar uma classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> que usa o contrato de serviço para escutar as solicitações de criação de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-110">This topic will walk you through creating a simple workflow, defining a service contract a client can use to activate the workflow, and deriving a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> which uses the service contract to listen for workflow creating requests.</span></span>  
  
### <a name="create-a-simple-workflow"></a><span data-ttu-id="91264-111">Criar um fluxo de trabalho simple</span><span class="sxs-lookup"><span data-stu-id="91264-111">Create a simple workflow</span></span>  
  
1.  <span data-ttu-id="91264-112">Criar um novo [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] vazio solução chamada `CreationEndpointTest`.</span><span class="sxs-lookup"><span data-stu-id="91264-112">Create a new [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] empty solution called `CreationEndpointTest`.</span></span>  
  
2.  <span data-ttu-id="91264-113">Adicionar um novo projeto de aplicativo de serviço de fluxo de trabalho WCF chamado `SimpleWorkflow` à solução.</span><span class="sxs-lookup"><span data-stu-id="91264-113">Add a new WCF Workflow Service Application project called `SimpleWorkflow` to the solution.</span></span> <span data-ttu-id="91264-114">O designer de fluxo de trabalho será aberta.</span><span class="sxs-lookup"><span data-stu-id="91264-114">The workflow designer will open.</span></span>  
  
3.  <span data-ttu-id="91264-115">Exclua as atividades ReceiveRequest e SendResponse.</span><span class="sxs-lookup"><span data-stu-id="91264-115">Delete the ReceiveRequest and SendResponse activities.</span></span> <span data-ttu-id="91264-116">Essas atividades são o que torna a um fluxo de trabalho como um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-116">These activities are what makes a workflow a workflow service.</span></span> <span data-ttu-id="91264-117">Como não estamos trabalhando com um serviço de fluxo de trabalho, não precisamos delas.</span><span class="sxs-lookup"><span data-stu-id="91264-117">Since we are not working with a workflow service, we no longer need them.</span></span>  
  
4.  <span data-ttu-id="91264-118">Defina o DisplayName da atividade de sequência para "Fluxo de trabalho sequencial".</span><span class="sxs-lookup"><span data-stu-id="91264-118">Set the DisplayName for the sequence activity to "Sequential Workflow".</span></span>  
  
5.  <span data-ttu-id="91264-119">Renomeie Service1.xamlx para Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="91264-119">Rename Service1.xamlx to Workflow1.xamlx.</span></span>  
  
6.  <span data-ttu-id="91264-120">O designer fora da atividade de sequência e definir as propriedades Name e ConfigurationName para "Workflow1"</span><span class="sxs-lookup"><span data-stu-id="91264-120">Click the designer outside of the sequence activity, and set the Name and ConfigurationName properties to "Workflow1"</span></span>  
  
7.  <span data-ttu-id="91264-121">Arraste um <xref:System.Activities.Statements.WriteLine> atividade de <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="91264-121">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="91264-122">O <xref:System.Activities.Statements.WriteLine> atividade pode ser encontrada no **primitivos** seção da caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="91264-122">The <xref:System.Activities.Statements.WriteLine> activity can be found in the **Primitives** section of the toolbox.</span></span> <span data-ttu-id="91264-123">Definir o <xref:System.Activities.Statements.WriteLine.Text%2A> propriedade o <xref:System.Activities.Statements.WriteLine> atividade para "Olá, mundo".</span><span class="sxs-lookup"><span data-stu-id="91264-123">Set the <xref:System.Activities.Statements.WriteLine.Text%2A> property of the <xref:System.Activities.Statements.WriteLine> activity to "Hello, world".</span></span>  
  
     <span data-ttu-id="91264-124">O fluxo de trabalho agora deve se parecer com o diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="91264-124">The workflow should now look like the following diagram.</span></span>  
  
     <span data-ttu-id="91264-125">![Um fluxo de trabalho simple](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "fluxo de trabalho simples")</span><span class="sxs-lookup"><span data-stu-id="91264-125">![A simple workflow](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span></span>  
  
### <a name="create-the-workflow-creation-service-contract"></a><span data-ttu-id="91264-126">Criar o contrato de serviço de criação do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="91264-126">Create the workflow creation service contract</span></span>  
  
1.  <span data-ttu-id="91264-127">Adicionar um novo projeto de biblioteca de classe chamado `Shared` para o `CreationEndpointTest` solução.</span><span class="sxs-lookup"><span data-stu-id="91264-127">Add a new class library project called `Shared` to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="91264-128">Adicione uma referência a System.ServiceModel.dll, System. Configuration e System.ServiceModel.Activities para o `Shared` projeto.</span><span class="sxs-lookup"><span data-stu-id="91264-128">Add a reference to System.ServiceModel.dll, System.Configuration, and System.ServiceModel.Activities to the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="91264-129">Renomeie o arquivo Class1.cs para IWorkflowCreation.cs e o código a seguir para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="91264-129">Rename the Class1.cs file to IWorkflowCreation.cs and the following code to the file.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     <span data-ttu-id="91264-130">Esse contrato define duas operações que ambos criam uma nova instância do fluxo de trabalho sem serviço recém-criado.</span><span class="sxs-lookup"><span data-stu-id="91264-130">This contract defines two operations both create a new instance of the non-service workflow you just created.</span></span> <span data-ttu-id="91264-131">Um cria uma nova instância com uma ID de instância gerado e o outro permite que você especifique a ID de instância para a nova instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-131">One creates a new instance with a generated instance ID and the other allows you to specify the instance ID for the new workflow instance.</span></span>  <span data-ttu-id="91264-132">Ambos os métodos permitem que você passar parâmetros para a nova instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-132">Both methods allow you to pass in parameters to the new workflow instance.</span></span> <span data-ttu-id="91264-133">Este contrato será exposto pelo <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para permitir que os clientes criar novas instâncias de fluxo de trabalho sem serviço.</span><span class="sxs-lookup"><span data-stu-id="91264-133">This contract will be exposed by the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to allow clients to create new instances of a non-service workflow.</span></span>  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a><span data-ttu-id="91264-134">Derive uma classe de WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="91264-134">Derive a class from WorkflowHostingEndpoint</span></span>  
  
1.  <span data-ttu-id="91264-135">Adicionar uma nova classe chamada `CreationEndpoint` derivado <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para o `Shared` projeto.</span><span class="sxs-lookup"><span data-stu-id="91264-135">Add a new class called `CreationEndpoint` derived from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to the `Shared` project.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="91264-136">Adicionar um local estático <xref:System.Uri> variável chamada `defaultBaseUri` para o `CreationEndpoint` classe.</span><span class="sxs-lookup"><span data-stu-id="91264-136">Add a local static <xref:System.Uri> variable called `defaultBaseUri` to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  <span data-ttu-id="91264-137">Adicione o seguinte construtor para o `CreationEndpoint` classe.</span><span class="sxs-lookup"><span data-stu-id="91264-137">Add the following constructor to the `CreationEndpoint` class.</span></span> <span data-ttu-id="91264-138">Observe que especificamos o `IWorkflowCreation` contrato de serviço na chamada para o construtor base.</span><span class="sxs-lookup"><span data-stu-id="91264-138">Notice we specify the `IWorkflowCreation` service contract in the call to the base constructor.</span></span>  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  <span data-ttu-id="91264-139">Adicione o seguinte construtor padrão para o `CreationEndpoint` classe.</span><span class="sxs-lookup"><span data-stu-id="91264-139">Add the following default constructor to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  <span data-ttu-id="91264-140">Adicionar um estático `DefaultBaseUri` propriedade para o `CreationEndpoint` classe.</span><span class="sxs-lookup"><span data-stu-id="91264-140">Add a static `DefaultBaseUri` property to the `CreationEndpoint` class.</span></span> <span data-ttu-id="91264-141">Essa propriedade será usada para manter um padrão URI de base se não for fornecido.</span><span class="sxs-lookup"><span data-stu-id="91264-141">This property will be used to hold a default base URI if one is not provided.</span></span>  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  <span data-ttu-id="91264-142">Crie o seguinte método para obter a associação padrão a ser usado para o ponto de extremidade de criação.</span><span class="sxs-lookup"><span data-stu-id="91264-142">Create the following method to get the default binding to use for the creation endpoint.</span></span>  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  <span data-ttu-id="91264-143">Substituir o <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> método para retornar a ID de instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="91264-143">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> method to return the workflow instance ID.</span></span> <span data-ttu-id="91264-144">Se o `Action` cabeçalho termina com "Criar" retorna um GUID vazio, se o `Action` cabeçalho termina com o GUID é passado para o método de retorno de "CreateWithInstanceId".</span><span class="sxs-lookup"><span data-stu-id="91264-144">If the `Action` header ends with "Create" return an empty GUID, if the `Action` header ends with "CreateWithInstanceId" return the GUID passed into the method.</span></span> <span data-ttu-id="91264-145">Caso contrário, gerar um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="91264-145">Otherwise, throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="91264-146">Essas `Action` cabeçalhos correspondem às duas operações definidas no `IWorkflowCreation` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="91264-146">These `Action` headers correspond to the two operations defined in the `IWorkflowCreation` service contract.</span></span>  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  <span data-ttu-id="91264-147">Substituir o <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> método para criar um <xref:System.ServiceModel.Activities.WorkflowCreationContext> e adicionar argumentos para o fluxo de trabalho, enviar a ID de instância para o cliente e, em seguida, retornar o <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span><span class="sxs-lookup"><span data-stu-id="91264-147">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> method to create a <xref:System.ServiceModel.Activities.WorkflowCreationContext> and add any arguments for the workflow, send the instance ID to the client, and then return the <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span></span>  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a><span data-ttu-id="91264-148">Criar um elemento de ponto de extremidade padrão para permitir que você configure o WorkflowCreationEndpoint</span><span class="sxs-lookup"><span data-stu-id="91264-148">Create a standard endpoint element to allow you to configure the WorkflowCreationEndpoint</span></span>  
  
1.  <span data-ttu-id="91264-149">Adicione uma referência ao compartilhado no `CreationEndpoint` projeto</span><span class="sxs-lookup"><span data-stu-id="91264-149">Add a reference to Shared in the `CreationEndpoint` project</span></span>  
  
2.  <span data-ttu-id="91264-150">Adicionar uma nova classe chamada `CreationEndpointElement`, derivada de <xref:System.ServiceModel.Configuration.StandardEndpointElement> para o `CreationEndpoint` projeto.</span><span class="sxs-lookup"><span data-stu-id="91264-150">Add a new class called `CreationEndpointElement`, derived from <xref:System.ServiceModel.Configuration.StandardEndpointElement> to the `CreationEndpoint` project.</span></span> <span data-ttu-id="91264-151">Essa classe representa um `CreationEndpoint` em um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="91264-151">This class will represent a `CreationEndpoint` in a web.config file.</span></span>  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  <span data-ttu-id="91264-152">Adicionar uma propriedade chamada `EndpointType` para retornar o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="91264-152">Add a property called `EndpointType` to return the type of the endpoint.</span></span>  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  <span data-ttu-id="91264-153">Substituir o <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> método e retorna um novo `CreationEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="91264-153">Override the <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> method and return a new `CreationEndpoint`.</span></span>  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  <span data-ttu-id="91264-154">Sobrecarga de <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, e <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="91264-154">Overload the <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, and <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> methods.</span></span> <span data-ttu-id="91264-155">Esses métodos apenas precisam ser definidos, não é preciso adicionar qualquer código para eles.</span><span class="sxs-lookup"><span data-stu-id="91264-155">These methods just need to be defined, you do not need to add any code to them.</span></span>  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  <span data-ttu-id="91264-156">Adicione a classe de coleção para `CreationEndpoint` para o arquivo CreationEndpointElement.cs no `CreationEndpoint` projeto.</span><span class="sxs-lookup"><span data-stu-id="91264-156">Add the collection class for `CreationEndpoint` to the CreationEndpointElement.cs file in the `CreationEndpoint` project.</span></span> <span data-ttu-id="91264-157">Essa classe é usada por configuração para manter um número de `CreationEndpoint` instâncias em um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="91264-157">This class is used by configuration to hold a number of `CreationEndpoint` instances in a web.config file.</span></span>  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="91264-158">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="91264-158">Build the solution.</span></span>  
  
### <a name="host-the-workflow-in-iis"></a><span data-ttu-id="91264-159">Host de fluxo de trabalho no IIS</span><span class="sxs-lookup"><span data-stu-id="91264-159">Host the workflow in IIS</span></span>  
  
1.  <span data-ttu-id="91264-160">Criar um novo aplicativo chamado `MyCreationEndpoint` no IIS.</span><span class="sxs-lookup"><span data-stu-id="91264-160">Create a new application called `MyCreationEndpoint` in IIS.</span></span>  
  
2.  <span data-ttu-id="91264-161">Copie o arquivo workflow1.xaml gerado pelo designer de fluxo de trabalho para o diretório de aplicativo e renomeie-o para workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="91264-161">Copy the workflow1.xaml file generated by the workflow designer to the application directory and rename it to workflow1.xamlx.</span></span>  
  
3.  <span data-ttu-id="91264-162">Copie os arquivos de CreationEndpoint.dll e shared.dll para o diretório bin do aplicativo (criar o diretório bin se não estiver presente).</span><span class="sxs-lookup"><span data-stu-id="91264-162">Copy the shared.dll and CreationEndpoint.dll files to the application’s bin directory (create the bin directory if it is not present).</span></span>  
  
4.  <span data-ttu-id="91264-163">Substitua o conteúdo do arquivo Web. config no `CreationEndpoint` projeto com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="91264-163">Replace the contents of the Web.config file in the `CreationEndpoint` project with the following code.</span></span>  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  <span data-ttu-id="91264-164">Após o `<system.web>` elemento, registrar `CreationEndpoint` adicionando o seguinte código de configuração.</span><span class="sxs-lookup"><span data-stu-id="91264-164">After the `<system.web>` element, register `CreationEndpoint` by adding the following configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="91264-165">Isso registra o `CreationEndpointCollection` de classe para que você possa configurar um `CreationEndpoint` em um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="91264-165">This registers the `CreationEndpointCollection` class so you can configure a `CreationEndpoint` in a web.config file.</span></span>  
  
6.  <span data-ttu-id="91264-166">Adicionar um `<service>` elemento (após o \</extensions > marca) com um `CreationEndpoint` que vai escutar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="91264-166">Add a `<service>` element (after the \</extensions> tag) with a `CreationEndpoint` which will listen for incoming messages.</span></span>  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  <span data-ttu-id="91264-167">Adicionar um \<comportamentos > elemento (após o  \< /services > marca) para habilitar metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="91264-167">Add a \<behaviors> element (after the \</services> tag) to enable service metadata.</span></span>  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  <span data-ttu-id="91264-168">Copie o Web. config para seu diretório de aplicativo do IIS.</span><span class="sxs-lookup"><span data-stu-id="91264-168">Copy the web.config to your IIS application directory.</span></span>  
  
9. <span data-ttu-id="91264-169">Teste para ver se o ponto de extremidade de criação está funcionando, inicie o Internet Explorer e navegando até http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="91264-169">Test to see if the creation endpoint is working by starting Internet Explorer and browsing to http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span></span> <span data-ttu-id="91264-170">O Internet Explorer deve exibir a tela a seguir:</span><span class="sxs-lookup"><span data-stu-id="91264-170">Internet Explorer should display the following screen:</span></span>  
  
     <span data-ttu-id="91264-171">![Testando o serviço](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span><span class="sxs-lookup"><span data-stu-id="91264-171">![Testing the service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span></span>  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a><span data-ttu-id="91264-172">Crie um cliente que chamará o CreationEndpoint.</span><span class="sxs-lookup"><span data-stu-id="91264-172">Create a client that will call the CreationEndpoint.</span></span>  
  
1.  <span data-ttu-id="91264-173">Adicionar um novo aplicativo de Console para o `CreationEndpointTest` solução.</span><span class="sxs-lookup"><span data-stu-id="91264-173">Add a new Console application to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="91264-174">Adicione referências a System.ServiceModel.dll, System.ServiceModel.Activities e o `Shared` projeto.</span><span class="sxs-lookup"><span data-stu-id="91264-174">Add references to System.ServiceModel.dll, System.ServiceModel.Activities, and the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="91264-175">No `Main` método cria um <xref:System.ServiceModel.ChannelFactory%601> do tipo `IWorkflowCreation` e chame <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span><span class="sxs-lookup"><span data-stu-id="91264-175">In the `Main` method create a <xref:System.ServiceModel.ChannelFactory%601> of type `IWorkflowCreation` and call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span></span> <span data-ttu-id="91264-176">Isso retornará um proxy.</span><span class="sxs-lookup"><span data-stu-id="91264-176">This will return a proxy.</span></span> <span data-ttu-id="91264-177">Em seguida, você pode chamar `Create` no proxy para criar a instância de fluxo de trabalho hospedados no IIS:</span><span class="sxs-lookup"><span data-stu-id="91264-177">You can then call `Create` on that proxy to create the workflow instance hosted under IIS:</span></span>  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="91264-178">Execute o CreationEndpointClient.</span><span class="sxs-lookup"><span data-stu-id="91264-178">Run the CreationEndpointClient.</span></span> <span data-ttu-id="91264-179">A saída deve se parecer com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="91264-179">The output should look like the following:</span></span>  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="91264-180">Você não verá a saída do fluxo de trabalho porque ele está em execução no IIS que não tem nenhuma saída de console.</span><span class="sxs-lookup"><span data-stu-id="91264-180">You will not see the output of the workflow because it is running under IIS which has no console output.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91264-181">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91264-181">Example</span></span>  
 <span data-ttu-id="91264-182">Este é o código completo para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="91264-182">The following is the complete code for this sample.</span></span>  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="91264-183">Este exemplo pode parecer confuso, pois implementem um serviço que implementa `IWorkflowCreation`.</span><span class="sxs-lookup"><span data-stu-id="91264-183">This example may seem confusing because you never implement a service that implements `IWorkflowCreation`.</span></span> <span data-ttu-id="91264-184">Isso ocorre porque o `CreationEndpoint` faz isso para você.</span><span class="sxs-lookup"><span data-stu-id="91264-184">This is because the `CreationEndpoint` does this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91264-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91264-185">See Also</span></span>  
 [<span data-ttu-id="91264-186">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="91264-186">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="91264-187">Hospedagem nos Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="91264-187">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="91264-188">Práticas recomendadas de hospedagem de Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="91264-188">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="91264-189">Instruções de hospedagem do Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="91264-189">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="91264-190">Arquitetura do Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="91264-190">Windows Workflow Architecture</span></span>](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [<span data-ttu-id="91264-191">Indicador de resumo de WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="91264-191">WorkflowHostingEndpoint Resume Bookmark</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [<span data-ttu-id="91264-192">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="91264-192">Rehosting the Workflow Designer</span></span>](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="91264-193">Visão geral do Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="91264-193">Windows Workflow Overview</span></span>](../../../../docs/framework/windows-workflow-foundation/overview.md)
