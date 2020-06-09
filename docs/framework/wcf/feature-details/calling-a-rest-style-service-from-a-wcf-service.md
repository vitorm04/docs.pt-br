---
title: Chamando um serviço REST-style de um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: eaa5d08faa335740124fcf698b22d2d324cd2c54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576480"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="cdd49-102">Chamando um serviço REST-style de um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="cdd49-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="cdd49-103">Ao chamar um serviço estilo REST de um serviço WCF regular (baseado em SOAP), o contexto de operação no método de serviço (que contém informações sobre a solicitação de entrada) substitui o contexto que deve ser usado pela solicitação de saída.</span><span class="sxs-lookup"><span data-stu-id="cdd49-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="cdd49-104">Isso faz com que as solicitações HTTP GET sejam alteradas para solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="cdd49-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="cdd49-105">Para forçar o serviço WCF a usar o contexto certo para chamar o serviço estilo REST, crie um novo <xref:System.ServiceModel.OperationContextScope> e chame o serviço estilo REST de dentro do escopo de contexto de operação.</span><span class="sxs-lookup"><span data-stu-id="cdd49-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="cdd49-106">Este tópico descreverá como criar um exemplo simples que ilustra essa técnica.</span><span class="sxs-lookup"><span data-stu-id="cdd49-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="cdd49-107">Definir o contrato de serviço estilo REST</span><span class="sxs-lookup"><span data-stu-id="cdd49-107">Define the REST-style service contract</span></span>

<span data-ttu-id="cdd49-108">Definir um contrato de serviço de estilo REST simples:</span><span class="sxs-lookup"><span data-stu-id="cdd49-108">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="cdd49-109">Implementar o contrato de serviço estilo REST</span><span class="sxs-lookup"><span data-stu-id="cdd49-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="cdd49-110">Implementar o contrato de serviço estilo REST:</span><span class="sxs-lookup"><span data-stu-id="cdd49-110">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="cdd49-111">Definir o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="cdd49-111">Define the WCF service contract</span></span>

<span data-ttu-id="cdd49-112">Defina um contrato de serviço WCF que será usado para chamar o serviço estilo REST:</span><span class="sxs-lookup"><span data-stu-id="cdd49-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="cdd49-113">Implementar o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="cdd49-113">Implement the WCF service contract</span></span>

<span data-ttu-id="cdd49-114">Implementar o contrato de serviço do WCF:</span><span class="sxs-lookup"><span data-stu-id="cdd49-114">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="cdd49-115">Criar o proxy do cliente para o serviço estilo REST</span><span class="sxs-lookup"><span data-stu-id="cdd49-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="cdd49-116">Usando <xref:System.ServiceModel.ClientBase%601> para implementar o proxy do cliente.</span><span class="sxs-lookup"><span data-stu-id="cdd49-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="cdd49-117">Para cada método chamado, um novo <xref:System.ServiceModel.OperationContextScope> é criado e usado para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="cdd49-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="cdd49-118">Hospedar e chamar os serviços</span><span class="sxs-lookup"><span data-stu-id="cdd49-118">Host and call the services</span></span>

<span data-ttu-id="cdd49-119">Hospede ambos os serviços em um aplicativo de console, adicionando os pontos de extremidade e comportamentos necessários.</span><span class="sxs-lookup"><span data-stu-id="cdd49-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="cdd49-120">Em seguida, chame o serviço WCF regular:</span><span class="sxs-lookup"><span data-stu-id="cdd49-120">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="cdd49-121">Listagem de código completo</span><span class="sxs-lookup"><span data-stu-id="cdd49-121">Complete code listing</span></span>

<span data-ttu-id="cdd49-122">Veja a seguir uma lista completa do exemplo implementado neste tópico:</span><span class="sxs-lookup"><span data-stu-id="cdd49-122">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cdd49-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdd49-123">See also</span></span>

- [<span data-ttu-id="cdd49-124">Como criar um serviço Web HTTP WCF básico</span><span class="sxs-lookup"><span data-stu-id="cdd49-124">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="cdd49-125">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="cdd49-125">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
