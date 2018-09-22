---
title: Acessando OperationContext por meio de um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: b1dafe55-a20e-4db0-9ac8-90c315883cdd
ms.openlocfilehash: 15dd817dddbe3272b188f6b74697f8c5839d498b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697822"
---
# <a name="accessing-operationcontext-from-a-workflow-service"></a><span data-ttu-id="99884-102">Acessando OperationContext por meio de um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="99884-102">Accessing OperationContext from a Workflow Service</span></span>
<span data-ttu-id="99884-103">Para acessar o <xref:System.ServiceModel.OperationContext> dentro de um serviço de fluxo de trabalho, você deve implementar o <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface em uma propriedade de execução personalizado.</span><span class="sxs-lookup"><span data-stu-id="99884-103">To access the <xref:System.ServiceModel.OperationContext> inside a workflow service, you must implement the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface in a custom execution property.</span></span> <span data-ttu-id="99884-104">Substituir a <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> método que é passado uma referência para o <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="99884-104">Override the <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> method which is passed a reference to the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="99884-105">Este tópico orientará você por meio de implementar essa propriedade de execução para recuperar um cabeçalho personalizado, bem como uma atividade personalizada que serão exibidos essa propriedade para o <xref:System.ServiceModel.Activities.Receive> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99884-105">This topic will walk you through implementing this execution property to retrieve a custom header, as well as a custom activity that will surface this property to the <xref:System.ServiceModel.Activities.Receive> at runtime.</span></span>  <span data-ttu-id="99884-106">A atividade personalizado implementará o mesmo comportamento que um <xref:System.Activities.Statements.Sequence> atividade, exceto que, quando um <xref:System.ServiceModel.Activities.Receive> é colocado dentro dela, o <xref:System.ServiceModel.Activities.IReceiveMessageCallback> será chamado e o <xref:System.ServiceModel.OperationContext> informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="99884-106">The custom activity will implement the same behavior as a <xref:System.Activities.Statements.Sequence> activity, except that when a <xref:System.ServiceModel.Activities.Receive> is placed inside of it, the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> will be called and the <xref:System.ServiceModel.OperationContext> information will be retrieved.</span></span>  <span data-ttu-id="99884-107">Este tópico também mostra como acessar o lado do cliente <xref:System.ServiceModel.OperationContext> para adicionar cabeçalhos de saída por meio de <xref:System.ServiceModel.Activities.ISendMessageCallback> interface.</span><span class="sxs-lookup"><span data-stu-id="99884-107">This topic also shows how to access the client-side <xref:System.ServiceModel.OperationContext> to add outgoing headers via the <xref:System.ServiceModel.Activities.ISendMessageCallback> interface.</span></span>  
  
### <a name="implement-the-service-side-ireceivemessagecallback"></a><span data-ttu-id="99884-108">Implementar o IReceiveMessageCallback do lado do serviço</span><span class="sxs-lookup"><span data-stu-id="99884-108">Implement the Service-side IReceiveMessageCallback</span></span>  
  
1.  <span data-ttu-id="99884-109">Criar um vazio [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solução.</span><span class="sxs-lookup"><span data-stu-id="99884-109">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution.</span></span>  
  
2.  <span data-ttu-id="99884-110">Adicionar um novo aplicativo de console chamado `Service` à solução.</span><span class="sxs-lookup"><span data-stu-id="99884-110">Add a new console application called `Service` to the solution.</span></span>  
  
3.  <span data-ttu-id="99884-111">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="99884-111">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="99884-112">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="99884-112">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="99884-113">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99884-113">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="99884-114">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="99884-114">System.ServiceModel.Activities</span></span>  
  
4.  <span data-ttu-id="99884-115">Adicionar uma nova classe chamada `ReceiveInstanceIdCallback` e implementar <xref:System.ServiceModel.Activities.IReceiveMessageCallback> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="99884-115">Add a new class called `ReceiveInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.IReceiveMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
          public const string HeaderName = "InstanceIdHeader";  
          public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
         public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
          {              
                try  
                {  
                    Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                    Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
                }  
                catch (MessageHeaderException)  
                {  
                    Console.WriteLine("This message must not be from a workflow.");  
                }  
            }  
    }  
    ```  
  
     <span data-ttu-id="99884-116">Esse código usa o <xref:System.ServiceModel.OperationContext> passado para o método para acessar os cabeçalhos da mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="99884-116">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to access the incoming message’s headers.</span></span>  
  
### <a name="implement-a-service-side-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="99884-117">Implementar uma atividade nativa do lado do serviço para adicionar a implementação de IReceiveMessageCallback para o NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="99884-117">Implement a Service-side Native activity to add the IReceiveMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="99884-118">Adicionar uma nova classe derivada <xref:System.Activities.NativeActivity> chamado `ReceiveInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="99884-118">Add a new class derived from <xref:System.Activities.NativeActivity> called `ReceiveInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="99884-119">Adicionar variáveis de locais para manter o controle de atividades filhas, variáveis, o índice da atividade atual e um <xref:System.Activities.CompletionCallback> retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="99884-119">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="99884-120">Implementar o construtor</span><span class="sxs-lookup"><span data-stu-id="99884-120">Implement the constructor</span></span>  
  
    ```  
    public ReceiveInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    }  
    ```  
  
4.  <span data-ttu-id="99884-121">Implemente a `Activities` e `Variables` propriedades.</span><span class="sxs-lookup"><span data-stu-id="99884-121">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="99884-122">Substituir <xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="99884-122">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="99884-123">Substituir <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="99884-123">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    ```  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="99884-124">Implementar o serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="99884-124">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="99884-125">Abrir existente `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="99884-125">Open the existing `Program` class.</span></span>  
  
2.  <span data-ttu-id="99884-126">Defina as seguintes constantes:</span><span class="sxs-lookup"><span data-stu-id="99884-126">Define the following constants:</span></span>  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  <span data-ttu-id="99884-127">Adicione um método estático chamado `GetWorkflowService` que cria o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="99884-127">Add a static method called `GetWorkflowService` that creates the workflow service.</span></span>  
  
    ```  
    static Activity GetServiceWorkflow()  
            {  
                Variable<string> echoString = new Variable<string>();  
  
                Receive echoRequest = new Receive  
                {  
                    CanCreateInstance = true,  
                    ServiceContractName = contract,  
                    OperationName = "Echo",  
                    Content = new ReceiveParametersContent()  
                    {  
                        Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                    }  
                };  
  
                return new ReceiveInstanceIdScope  
                {  
                    Variables = { echoString },  
                    Activities =  
                    {  
                        echoRequest,  
                        new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                        new SendReply  
                        {  
                            Request = echoRequest,  
                            Content = new SendParametersContent()  
                            {  
                                Parameters = { { "result", new InArgument<string>(echoString) } }   
                            }  
                        }  
                    }  
                };  
            }  
    ```  
  
4.  <span data-ttu-id="99884-128">Existente `Main` método, o serviço de fluxo de trabalho do host.</span><span class="sxs-lookup"><span data-stu-id="99884-128">In the existing `Main` method, host the workflow service.</span></span>  
  
    ```  
    static void Main(string[] args)  
            {  
                string addr = "http://localhost:8080/Service";  
  
                using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
                {  
                    host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
                    host.Open();  
                    Console.WriteLine("Service waiting at: " + addr);  
                    Console.WriteLine("Press [ENTER] to exit");  
                    Console.ReadLine();  
                    host.Close();  
                }  
            }  
    ```  
  
### <a name="implement-the-client-side-isendmessagecallback"></a><span data-ttu-id="99884-129">Implementar o ISendMessageCallback do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="99884-129">Implement the Client-side ISendMessageCallback</span></span>  
  
1.  <span data-ttu-id="99884-130">Adicionar um novo aplicativo de console chamado `Service` à solução.</span><span class="sxs-lookup"><span data-stu-id="99884-130">Add a new console application called `Service` to the solution.</span></span>  
  
2.  <span data-ttu-id="99884-131">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="99884-131">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="99884-132">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="99884-132">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="99884-133">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99884-133">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="99884-134">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="99884-134">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="99884-135">Adicionar uma nova classe chamada `SendInstanceIdCallback` e implementar <xref:System.ServiceModel.Activities.ISendMessageCallback> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="99884-135">Add a new class called `SendInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.ISendMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class SendInstanceIdCallback : ISendMessageCallback  
        {  
            public const string HeaderName = "InstanceIdHeader";  
            public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
            public Guid InstanceId { get; set; }  
  
            public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
            {  
                operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
            }  
        }  
    ```  
  
     <span data-ttu-id="99884-136">Esse código usa o <xref:System.ServiceModel.OperationContext> passado para o método para adicionar um cabeçalho personalizado para a mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="99884-136">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to add a custom header to the incoming message.</span></span>  
  
### <a name="implement-a-client-side-native-activity-to-add-the-client-side-isendmessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="99884-137">Implementar uma atividade nativa do lado do cliente para adicionar a implementação de ISendMessageCallback do lado do cliente para o NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="99884-137">Implement a Client-side Native activity to add the client-side ISendMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="99884-138">Adicionar uma nova classe derivada <xref:System.Activities.NativeActivity> chamado `SendInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="99884-138">Add a new class derived from <xref:System.Activities.NativeActivity> called `SendInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="99884-139">Adicionar variáveis de locais para manter o controle de atividades filhas, variáveis, o índice da atividade atual e um <xref:System.Activities.CompletionCallback> retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="99884-139">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class SendInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="99884-140">Implementar o construtor</span><span class="sxs-lookup"><span data-stu-id="99884-140">Implement the constructor</span></span>  
  
    ```  
    public SendInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    ```  
  
4.  <span data-ttu-id="99884-141">Implemente a `Activities` e `Variables` propriedades.</span><span class="sxs-lookup"><span data-stu-id="99884-141">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="99884-142">Substituir <xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="99884-142">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="99884-143">Substituir <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="99884-143">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
                InternalExecute(context, null);  
            }  
  
            void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
            {  
                //grab the index of the current Activity  
                int currentActivityIndex = this.currentIndex.Get(context);  
                if (currentActivityIndex == Activities.Count)  
                {  
                    //if the currentActivityIndex is equal to the count of MySequence's Activities  
                    //MySequence is complete  
                    return;  
                }  
  
                if (this.onChildComplete == null)  
                {  
                    //on completion of the current child, have the runtime call back on this method  
                    this.onChildComplete = new CompletionCallback(InternalExecute);  
                }  
  
                //grab the next Activity in MySequence.Activities and schedule it  
                Activity nextChild = Activities[currentActivityIndex];  
                context.ScheduleActivity(nextChild, this.onChildComplete);  
  
                //increment the currentIndex  
                this.currentIndex.Set(context, ++currentActivityIndex);  
            }  
    ```  
  
### <a name="implement-a-workflow-client"></a><span data-ttu-id="99884-144">Implementar um cliente de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="99884-144">Implement a workflow client</span></span>  
  
1.  <span data-ttu-id="99884-145">Criar um novo projeto de aplicativo de console chamado `Client`.</span><span class="sxs-lookup"><span data-stu-id="99884-145">Create a new console application project called `Client`.</span></span>  
  
2.  <span data-ttu-id="99884-146">Adicione referências aos assemblies a seguir:</span><span class="sxs-lookup"><span data-stu-id="99884-146">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="99884-147">System.Activities</span><span class="sxs-lookup"><span data-stu-id="99884-147">System.Activities</span></span>  
  
    2.  <span data-ttu-id="99884-148">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99884-148">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="99884-149">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="99884-149">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="99884-150">Abra o arquivo Program.cs gerado e adicione um método estático chamado `GetClientWorkflow` para criar o fluxo de trabalho do cliente.</span><span class="sxs-lookup"><span data-stu-id="99884-150">Open the generated Program.cs file and add a static method called `GetClientWorkflow` to create the client workflow.</span></span>  
  
    ```  
    static Activity GetClientWorkflow()  
            {  
                Variable<string> echoString = new Variable<string>();  
  
                // Define the endpoint  
                Endpoint clientEndpoint = new Endpoint  
                {  
                    Binding = new BasicHttpBinding(),  
                    AddressUri = new Uri("http://localhost:8080/Service")  
                };  
  
                // Configure the Send activity used to send a message  
                Send echoRequest = new Send  
                {  
                    Endpoint = clientEndpoint,  
                    ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                    OperationName = "Echo",  
                    Content = new SendParametersContent()  
                    {  
                        Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                    }  
                };  
  
                // Place the Send activity in a SendInstanceIdScope. This hooks up the ISendMessageCallback   
                // implementation to the client workflow.  
                return new SendInstanceIdScope  
                {  
                    Variables = { echoString },  
                    Activities =  
                    {                      
                        new CorrelationScope  
                        {  
                            Body = new Sequence  
                            {  
                                Activities =   
                                {  
                                    // Send the request message  
                                    echoRequest,  
  
                                   // Receive the reply from the service  
                                    new ReceiveReply  
                                    {  
                                        Request = echoRequest,  
                                        Content = new ReceiveParametersContent  
                                        {  
                                            Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                        }  
                                    }  
                                }  
                            }  
                        },                      
                        new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                    }  
                };  
            }  
    ```  
  
4.  <span data-ttu-id="99884-151">Adicione o seguinte código de hospedagem para o `Main()` método.</span><span class="sxs-lookup"><span data-stu-id="99884-151">Add the following hosting code to the `Main()` method.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="99884-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99884-152">Example</span></span>  
 <span data-ttu-id="99884-153">Aqui está uma listagem completa da fonte de código usado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="99884-153">Here is a complete listing of the source code used in this topic.</span></span>  
  
```  
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public ReceiveInstanceIdScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }                     
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {              
            try  
            {  
                Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
        }  
    }  
}  
```  
  
```  
// Service.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{      
    class Program  
    {  
        const string addr = "http://localhost:8080/Service";  
        static XName contract = XName.Get("IService", "http://tempuri.org");  
  
        static void Main(string[] args)  
        {  
            string addr = "http://localhost:8080/Service";  
  
            using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
            {  
                host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
                host.Open();  
                Console.WriteLine("Service waiting at: " + addr);  
                Console.WriteLine("Press [ENTER] to exit");  
                Console.ReadLine();  
                host.Close();  
            }  
  
        }  
  
        static Activity GetServiceWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Receive echoRequest = new Receive  
            {  
                CanCreateInstance = true,  
                ServiceContractName = contract,  
                OperationName = "Echo",  
                Content = new ReceiveParametersContent()  
                {  
                    Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                }  
            };  
  
            return new ReceiveInstanceIdScope  
            {  
                Variables = { echoString },  
                Activities =  
                {  
                    echoRequest,  
                    new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                    new SendReply  
                    {  
                        Request = echoRequest,  
                        Content = new SendParametersContent()  
                        {  
                            Parameters = { { "result", new InArgument<string>(echoString) } }   
                        }  
                    }  
                }  
            };  
        }  
    }  
  
}  
```  
  
```  
// SendInstanceIdCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class SendInstanceIdCallback : ISendMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public Guid InstanceId { get; set; }  
  
        public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
        {  
            operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
        }  
    }  
}  
```  
  
```  
// SendInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    public sealed class SendInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public SendInstanceIdScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }  
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// Client.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Activity workflow = GetClientWorkflow();  
            WorkflowInvoker.Invoke(workflow);  
            WorkflowInvoker.Invoke(workflow);  
            Console.WriteLine("Press [ENTER] to exit");  
            Console.ReadLine();  
        }  
  
        static Activity GetClientWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Endpoint clientEndpoint = new Endpoint  
            {  
                Binding = new BasicHttpBinding(),  
                AddressUri = new Uri("http://localhost:8080/Service")  
            };  
  
            Send echoRequest = new Send  
            {  
                Endpoint = clientEndpoint,  
                ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                OperationName = "Echo",  
                Content = new SendParametersContent()  
                {  
                    Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                }  
            };  
  
            return new SendInstanceIdScope  
            {  
                Variables = { echoString },  
                Activities =  
                {                      
                    new CorrelationScope  
                    {  
                        Body = new Sequence  
                        {  
                            Activities =   
                            {  
                                echoRequest,  
                                new ReceiveReply  
                                {  
                                    Request = echoRequest,  
                                    Content = new ReceiveParametersContent  
                                    {  
                                        Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                    }  
                                }  
                            }  
                        }  
                    },                      
                    new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                }  
            };  
        }  
    }  
}  
```  
  
 <span data-ttu-id="99884-154">Comentários opcionais.</span><span class="sxs-lookup"><span data-stu-id="99884-154">Optional comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99884-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99884-155">See Also</span></span>  
 [<span data-ttu-id="99884-156">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="99884-156">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="99884-157">Acessando OperationContext</span><span class="sxs-lookup"><span data-stu-id="99884-157">Accessing OperationContext</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [<span data-ttu-id="99884-158">Criando fluxos de trabalho, atividades e expressões de design usando o código obrigatório</span><span class="sxs-lookup"><span data-stu-id="99884-158">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
