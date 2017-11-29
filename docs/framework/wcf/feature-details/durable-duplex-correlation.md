---
title: "Correlação duplex durável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc7a6655467fccf924783fea9110bdaf1b788675
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="71c5a-102">Correlação duplex durável</span><span class="sxs-lookup"><span data-stu-id="71c5a-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="71c5a-103">Correlação duplex durável, também conhecido como correlação de retorno de chamada, é útil quando um serviço de fluxo de trabalho tem um requisito para enviar um retorno de chamada para o chamador inicial.</span><span class="sxs-lookup"><span data-stu-id="71c5a-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="71c5a-104">Ao contrário de duplex do WCF, o retorno de chamada pode ocorrer a qualquer momento no futuro e não está vinculado para o mesmo canal ou o tempo de vida do canal; o único requisito é que o chamador tem um ponto de extremidade ativo escuta para a mensagem de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="71c5a-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="71c5a-105">Isso permite que os dois serviços de fluxo de trabalho para se comunicar em uma conversa de longa execução.</span><span class="sxs-lookup"><span data-stu-id="71c5a-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="71c5a-106">Este tópico fornece uma visão geral de correlação duplex durável.</span><span class="sxs-lookup"><span data-stu-id="71c5a-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="71c5a-107">Usando a correlação Duplex durável</span><span class="sxs-lookup"><span data-stu-id="71c5a-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="71c5a-108">Para usar a correlação duplex durável, os dois serviços devem usar uma associação de contexto habilitado que oferece suporte a operações de duas vias, como <xref:System.ServiceModel.NetTcpContextBinding> ou <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="71c5a-109">Os registros de serviço chamada um <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> com a associação desejada no seu cliente <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="71c5a-110">O serviço de recebimento recebe esses dados na chamada inicial e, em seguida, usa-lo por conta própria <xref:System.ServiceModel.Endpoint> no <xref:System.ServiceModel.Activities.Send> atividade que faz a chamada para o serviço de chamada.</span><span class="sxs-lookup"><span data-stu-id="71c5a-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="71c5a-111">Neste exemplo, dois serviços se comuniquem entre si.</span><span class="sxs-lookup"><span data-stu-id="71c5a-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="71c5a-112">O primeiro serviço invoca um método em um segundo serviço e, em seguida, aguarda uma resposta.</span><span class="sxs-lookup"><span data-stu-id="71c5a-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="71c5a-113">O segundo serviço sabe o nome do método de retorno de chamada, mas o ponto de extremidade do serviço que implementa este método não é conhecido em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="71c5a-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71c5a-114">Frente e verso durável só pode ser usado quando o <xref:System.ServiceModel.Channels.AddressingVersion> do ponto de extremidade é configurado com <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="71c5a-115">Se não estiver, então um <xref:System.InvalidOperationException> exceção será lançada com a seguinte mensagem: "a mensagem contém um cabeçalho de contexto de retorno de chamada com uma referência de ponto de extremidade para AddressingVersion ' Addressing200408 (HYPERLINK"http://schemas.xmlsoap.org/ws/2004/08/ endereçamento"http://schemas.xmlsoap.org/ws/2004/08/addressing)'.</span><span class="sxs-lookup"><span data-stu-id="71c5a-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for AddressingVersion 'Addressing200408 ( HYPERLINK "http://schemas.xmlsoap.org/ws/2004/08/addressing" http://schemas.xmlsoap.org/ws/2004/08/addressing)'.</span></span> <span data-ttu-id="71c5a-116">Contexto de retorno de chamada pode ser transmitido apenas quando a AddressingVersion está configurada com 'WSAddressing10'."</span><span class="sxs-lookup"><span data-stu-id="71c5a-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'."</span></span>  
  
 <span data-ttu-id="71c5a-117">No exemplo a seguir, um serviço de fluxo de trabalho está hospedado que cria um retorno de chamada <xref:System.ServiceModel.Endpoint> usando <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="71c5a-118">O fluxo de trabalho que implementa o serviço de fluxo de trabalho inicializa a correlação de retorno de chamada com seu <xref:System.ServiceModel.Activities.Send> atividade e faz referência a esse ponto de extremidade de retorno de chamada a <xref:System.ServiceModel.Activities.Receive> atividade que se correlaciona com o <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="71c5a-119">O exemplo a seguir representa o fluxo de trabalho que é retornado o `GetWF1` método.</span><span class="sxs-lookup"><span data-stu-id="71c5a-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")                          
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="71c5a-120">O segundo serviço de fluxo de trabalho é hospedado usando uma associação fornecida pelo sistema, com base em contexto.</span><span class="sxs-lookup"><span data-stu-id="71c5a-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="71c5a-121">O fluxo de trabalho que implementa o serviço de fluxo de trabalho começa com um <xref:System.ServiceModel.Activities.Receive> atividade.</span><span class="sxs-lookup"><span data-stu-id="71c5a-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="71c5a-122">Isso receber atividade inicializa a correlação de retorno de chamada para esse serviço, atrasos por um período de tempo para simular o trabalho de longa execução e, em seguida, chamadas de volta para o primeiro serviço usando o contexto de retorno de chamada que foi passado na primeira chamada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="71c5a-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="71c5a-123">O exemplo a seguir representa o fluxo de trabalho que é retornado de uma chamada para `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="71c5a-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="71c5a-124">Observe que o <xref:System.ServiceModel.Activities.Send> atividade tem um endereço de espaço reservado de `http://www.contoso.com`; o endereço real usado em tempo de execução é o endereço de retorno de chamada fornecido.</span><span class="sxs-lookup"><span data-stu-id="71c5a-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="71c5a-125">Quando o `StartOrder` método é invocado no primeiro fluxo de trabalho, a seguinte saída é exibida, que mostra o fluxo de execução por meio de dois fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="71c5a-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```Output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.   
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="71c5a-126">Neste exemplo, ambos os fluxos de trabalho de gerenciar explicitamente correlação usando um <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="71c5a-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="71c5a-127">Devido a apenas uma única correlação nesses fluxos de trabalho de exemplo, o padrão <xref:System.ServiceModel.Activities.CorrelationHandle> gerenciamento seria suficiente.</span><span class="sxs-lookup"><span data-stu-id="71c5a-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c5a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71c5a-128">See Also</span></span>  
 [<span data-ttu-id="71c5a-129">Frente e verso durável &#91; Exemplos de WF &#93;</span><span class="sxs-lookup"><span data-stu-id="71c5a-129">Durable Duplex &#91;WF Samples&#93;</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
