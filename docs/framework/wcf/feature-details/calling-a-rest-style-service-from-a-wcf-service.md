---
title: Chamando um serviço REST-style de um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: c2a3467fb5fe28194dcb8ee7715353f4cb6a1bff
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57842925"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="60a7c-102">Chamando um serviço REST-style de um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="60a7c-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="60a7c-103">Ao chamar um serviço estilo REST do serviço WCF (baseado em SOAP) regular, o contexto de operação no método de serviço (que contém informações sobre a solicitação de entrada) substitui o contexto que deve ser usado pela solicitação de saída.</span><span class="sxs-lookup"><span data-stu-id="60a7c-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="60a7c-104">Isso faz com que as solicitações HTTP GET alterar para solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="60a7c-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="60a7c-105">Para forçar o serviço do WCF para usar o contexto certo para chamar o serviço estilo REST, criar um novo <xref:System.ServiceModel.OperationContextScope> e chamar o serviço estilo REST de dentro do escopo de contexto de operação.</span><span class="sxs-lookup"><span data-stu-id="60a7c-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="60a7c-106">Este tópico descreve como criar um exemplo simple que ilustra essa técnica.</span><span class="sxs-lookup"><span data-stu-id="60a7c-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="60a7c-107">Definir o contrato de serviço no estilo REST</span><span class="sxs-lookup"><span data-stu-id="60a7c-107">Define the REST-style service contract</span></span>

<span data-ttu-id="60a7c-108">Defina um contrato de serviço no estilo REST simple:</span><span class="sxs-lookup"><span data-stu-id="60a7c-108">Define a simple  REST-style service contract:</span></span>

```csharp
[ServiceContract]
public interface IRestInterface
{
    [OperationContract, WebGet]
    int Add(int x, int y);

    [OperationContract, WebGet]
    string Echo(string input);
}
```

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="60a7c-109">Implementar o contrato de serviço no estilo REST</span><span class="sxs-lookup"><span data-stu-id="60a7c-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="60a7c-110">Implemente o contrato de serviço no estilo REST:</span><span class="sxs-lookup"><span data-stu-id="60a7c-110">Implement the REST-style service contract:</span></span>

```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }

    public string Echo(string input)
    {
        return input;
    }
}
```

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="60a7c-111">Definir o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="60a7c-111">Define the WCF service contract</span></span>

<span data-ttu-id="60a7c-112">Defina um contrato de serviço do WCF que será usado para chamar o serviço estilo REST:</span><span class="sxs-lookup"><span data-stu-id="60a7c-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);

    [OperationContract]
    string CallEcho(string input);
}
```

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="60a7c-113">Implementar o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="60a7c-113">Implement the WCF service contract</span></span>

<span data-ttu-id="60a7c-114">Implemente o contrato de serviço do WCF:</span><span class="sxs-lookup"><span data-stu-id="60a7c-114">Implement the WCF service contract:</span></span>

```csharp
public class NormalService : INormalInterface
{
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
    public int CallAdd(int x, int y)
    {
        return client.Add(x, y);
    }

    public string CallEcho(string input)
    {
        return client.Echo(input);
    }
}
```

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="60a7c-115">Criar o proxy de cliente para o serviço estilo REST</span><span class="sxs-lookup"><span data-stu-id="60a7c-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="60a7c-116">Usando <xref:System.ServiceModel.ClientBase%601> para implementar o proxy do cliente.</span><span class="sxs-lookup"><span data-stu-id="60a7c-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="60a7c-117">Para cada método de chamada, um novo <xref:System.ServiceModel.OperationContextScope> é criado e usado para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="60a7c-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```

## <a name="host-and-call-the-services"></a><span data-ttu-id="60a7c-118">Hospedar e chamar os serviços</span><span class="sxs-lookup"><span data-stu-id="60a7c-118">Host and call the services</span></span>

<span data-ttu-id="60a7c-119">Ambos os serviços em um aplicativo de console, adicionando os pontos de extremidade necessários e os comportamentos de host.</span><span class="sxs-lookup"><span data-stu-id="60a7c-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="60a7c-120">E, em seguida, chame o serviço WCF normal:</span><span class="sxs-lookup"><span data-stu-id="60a7c-120">And then call the regular WCF service:</span></span>

```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```

## <a name="complete-code-listing"></a><span data-ttu-id="60a7c-121">Listagem de código completa</span><span class="sxs-lookup"><span data-stu-id="60a7c-121">Complete code listing</span></span>

<span data-ttu-id="60a7c-122">A seguir está uma listagem completa do exemplo implementada neste tópico:</span><span class="sxs-lookup"><span data-stu-id="60a7c-122">The following is a complete listing of the sample implemented in this topic:</span></span>

```csharp
public class CallingRESTSample
{
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";

    [ServiceContract]
    public interface IRestInterface
    {
        [OperationContract, WebGet]
        int Add(int x, int y);
        [OperationContract, WebGet]
        string Echo(string input);
    }

    [ServiceContract]
    public interface INormalInterface
    {
        [OperationContract]
        int CallAdd(int x, int y);
        [OperationContract]
        string CallEcho(string input);
    }

    public class RestService : IRestInterface
    {
        public int Add(int x, int y)
        {
            return x + y;
        }

        public string Echo(string input)
        {
            return input;
        }
    }

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
    {
        public MyRestClient(string address)
            : base(new WebHttpBinding(), new EndpointAddress(address))
        {
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());
        }

        public int Add(int x, int y)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Add(x, y);
            }
        }

        public string Echo(string input)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Echo(input);
            }
        }
    }

    public class NormalService : INormalInterface
    {
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
        public int CallAdd(int x, int y)
        {
            return client.Add(x, y);
        }

        public string CallEcho(string input)
        {
            return client.Echo(input);
        }
    }

    public static void Main()
    {
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
        restHost.Open();

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
        normalHost.Open();

        Console.WriteLine("Hosts opened");

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
        INormalInterface proxy = factory.CreateChannel();

        Console.WriteLine(proxy.CallAdd(123, 456));
        Console.WriteLine(proxy.CallEcho("Hello world"));
    }
}
```

## <a name="see-also"></a><span data-ttu-id="60a7c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60a7c-123">See also</span></span>

- [<span data-ttu-id="60a7c-124">Como: Criar um serviço de Web HTTP WCF básico</span><span class="sxs-lookup"><span data-stu-id="60a7c-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="60a7c-125">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="60a7c-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
