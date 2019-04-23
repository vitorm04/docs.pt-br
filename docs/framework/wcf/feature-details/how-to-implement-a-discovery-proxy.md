---
title: 'Como: implementar um proxy de descoberta'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: b3e0b5cef01998c1e509586ba1fab3924eb7bc0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321010"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="0c1b7-102">Como: implementar um proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="0c1b7-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="0c1b7-103">Este tópico explica como implementar um proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="0c1b7-104">Para obter mais informações sobre o recurso de descoberta no Windows Communication Foundation (WCF), consulte [visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0c1b7-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="0c1b7-105">Um proxy de descoberta pode ser implementado com a criação de uma classe que estende o <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="0c1b7-106">Há uma série de outras classes de suporte definidos e usados neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="0c1b7-107">`OnResolveAsyncResult`, `OnFindAsyncResult` e `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="0c1b7-108">Essas classes implementam o <xref:System.IAsyncResult> interface.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="0c1b7-109">Para obter mais informações sobre <xref:System.IAsyncResult> ver [interface System. IAsyncResult](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="0c1b7-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="0c1b7-110">Implementar um proxy de descoberta é dividido em três partes principais neste tópico:</span><span class="sxs-lookup"><span data-stu-id="0c1b7-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

-   <span data-ttu-id="0c1b7-111">Defina uma classe que contém um armazenamento de dados e estende abstrata <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

-   <span data-ttu-id="0c1b7-112">Implementar o auxiliar `AsyncResult` classe.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-112">Implement the helper `AsyncResult` class.</span></span>

-   <span data-ttu-id="0c1b7-113">Hospede o Proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="0c1b7-114">Para criar um novo projeto de aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="0c1b7-114">To create a new console application project</span></span>

1. <span data-ttu-id="0c1b7-115">Inicie o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="0c1b7-116">Crie um novo projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-116">Create a new console application project.</span></span> <span data-ttu-id="0c1b7-117">Nomeie o projeto `DiscoveryProxy` e o nome da solução `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="0c1b7-118">Adicione as seguintes referências ao projeto</span><span class="sxs-lookup"><span data-stu-id="0c1b7-118">Add the following references to the project</span></span>

    1.  <span data-ttu-id="0c1b7-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="0c1b7-119">System.ServiceModel.dll</span></span>

    2.  <span data-ttu-id="0c1b7-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="0c1b7-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    >  <span data-ttu-id="0c1b7-121">Certifique-se de que você referencie a versão 4.0 ou superior desses assemblies.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="0c1b7-122">Para implementar a classe ProxyDiscoveryService</span><span class="sxs-lookup"><span data-stu-id="0c1b7-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="0c1b7-123">Adicionar um novo arquivo de código ao seu projeto e nomeie-a como DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="0c1b7-124">Adicione o seguinte `using` instruções DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="0c1b7-125">Derivar de `DiscoveryProxyService` de <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="0c1b7-126">Aplicar o `ServiceBehavior` atributo à classe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="0c1b7-127">Dentro de `DiscoveryProxy` classe define um dicionário para armazenar os serviços registrados.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="0c1b7-128">Defina um construtor que inicializa o dicionário.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-128">Define a constructor that initializes the dictionary.</span></span>

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="0c1b7-129">Para definir os métodos usados para atualizar o cache de proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="0c1b7-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="0c1b7-130">Implementar o `AddOnlineservice` método para adicionar serviços ao cache.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="0c1b7-131">Isso é chamado toda vez que o proxy recebe uma mensagem de comunicado.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-131">This is called every time the proxy receives an announcement message.</span></span>

    ```
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
            }
    ```

2. <span data-ttu-id="0c1b7-132">Implementar o `RemoveOnlineService` método que é usado para remover os serviços de cache.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                if (endpointDiscoveryMetadata != null)
                {
                    lock (this.onlineServices)
                    {
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                    }

                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
                }
            }
    ```

3. <span data-ttu-id="0c1b7-133">Implementar o `MatchFromOnlineService` métodos que tentam fazer a correspondência de um serviço com um serviço no dicionário.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```
    void MatchFromOnlineService(FindRequestContext findRequestContext)
            {
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                        {
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                        }
                    }
                }
            }
    ```

    ```
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
            {
                EndpointDiscoveryMetadata matchingEndpoint = null;
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (criteria.Address == endpointDiscoveryMetadata.Address)
                        {
                            matchingEndpoint = endpointDiscoveryMetadata;
                        }
                    }
                }
                return matchingEndpoint;
            }
    ```

4. <span data-ttu-id="0c1b7-134">Implementar o `PrintDiscoveryMetadata` dos quais a descoberta de proxy está fazendo de saída do método que fornece aos usuários com o texto do console.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
            {
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
                {
                    Console.WriteLine("** " + contractName.ToString());
                    break;
                }
                Console.WriteLine("**** Operation Completed");
            }
    ```

5. <span data-ttu-id="0c1b7-135">Adicione as seguintes classes AsyncResult para o DiscoveryProxyService.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="0c1b7-136">Essas classes são usadas para diferenciar entre os resultados da operação assíncrona diferentes.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
            {
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
            {
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnFindAsyncResult : AsyncResult
            {
                public OnFindAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnFindAsyncResult>(result);
                }
            }

            sealed class OnResolveAsyncResult : AsyncResult
            {
                EndpointDiscoveryMetadata matchingEndpoint;

                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.matchingEndpoint = matchingEndpoint;
                    this.Complete(true);
                }

                public static EndpointDiscoveryMetadata End(IAsyncResult result)
                {
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                    return thisPtr.matchingEndpoint;
                }
            }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="0c1b7-137">Para definir os métodos que implementam a funcionalidade de proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="0c1b7-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="0c1b7-138">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-139">Esse método é chamado quando o proxy de descoberta recebe uma mensagem de comunicado online.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2. <span data-ttu-id="0c1b7-140">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-141">Esse método é chamado quando o proxy de descoberta termina de processar uma mensagem de comunicado.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3. <span data-ttu-id="0c1b7-142">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-143">Esse método é chamado com a descoberta de proxy recebe uma mensagem de comunicado offline.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4. <span data-ttu-id="0c1b7-144">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-145">Esse método é chamado quando o proxy de descoberta termina de processar uma mensagem de comunicado offline.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5. <span data-ttu-id="0c1b7-146">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-147">Esse método é chamado quando o proxy de descoberta recebe uma solicitação de localização.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```
    // OnBeginFind method is called when a Probe request message is received by the Proxy
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
            {
                this.MatchFromOnlineService(findRequestContext);
                return new OnFindAsyncResult(callback, state);
            }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="0c1b7-148">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-149">Esse método é chamado quando o proxy de descoberta termina de processar uma solicitação de localização.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7. <span data-ttu-id="0c1b7-150">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-151">Esse método é chamado quando o proxy de descoberta recebe uma mensagem de resolução.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
            {
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
            }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="0c1b7-152">Substituir o método <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0c1b7-153">Esse método é chamado quando o proxy de descoberta termina de processar uma mensagem de resolução.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 <span data-ttu-id="0c1b7-154">OnBegin...</span><span class="sxs-lookup"><span data-stu-id="0c1b7-154">The OnBegin..</span></span> <span data-ttu-id="0c1b7-155">/ OnEnd...</span><span class="sxs-lookup"><span data-stu-id="0c1b7-155">/ OnEnd..</span></span> <span data-ttu-id="0c1b7-156">métodos de fornecem a lógica para as operações subsequentes de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="0c1b7-157">Por exemplo o <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> e <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> métodos implementam a lógica de localização para o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="0c1b7-158">Quando o proxy de descoberta recebe uma mensagem de teste, esses métodos são executados para enviar uma resposta de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="0c1b7-159">Você pode modificar a lógica de localização conforme desejado, por exemplo, você pode incorporar a correspondência por algoritmos ou metadados específicos do aplicativo XML de análise como parte de sua operação de localização personalizado de escopo.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="0c1b7-160">Para implementar a classe AsyncResult</span><span class="sxs-lookup"><span data-stu-id="0c1b7-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="0c1b7-161">Defina a classe base abstrata AsyncResult que é usado para derivar as várias classes de resultado assíncrono.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="0c1b7-162">Crie um novo arquivo de código chamado AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="0c1b7-163">Adicione o seguinte `using` instruções AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="0c1b7-164">Adicione a seguinte classe AsyncResult.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-164">Add the following AsyncResult class.</span></span>

    ```
    abstract class AsyncResult : IAsyncResult
        {
            AsyncCallback callback;
            bool completedSynchronously;
            bool endCalled;
            Exception exception;
            bool isCompleted;
            ManualResetEvent manualResetEvent;
            object state;
            object thisLock;

            protected AsyncResult(AsyncCallback callback, object state)
            {
                this.callback = callback;
                this.state = state;
                this.thisLock = new object();
            }

            public object AsyncState
            {
                get
                {
                    return state;
                }
            }

            public WaitHandle AsyncWaitHandle
            {
                get
                {
                    if (manualResetEvent != null)
                    {
                        return manualResetEvent;
                    }
                    lock (ThisLock)
                    {
                        if (manualResetEvent == null)
                        {
                            manualResetEvent = new ManualResetEvent(isCompleted);
                        }
                    }
                    return manualResetEvent;
                }
            }

            public bool CompletedSynchronously
            {
                get
                {
                    return completedSynchronously;
                }
            }

            public bool IsCompleted
            {
                get
                {
                    return isCompleted;
                }
            }

            object ThisLock
            {
                get
                {
                    return this.thisLock;
                }
            }

            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
                where TAsyncResult : AsyncResult
            {
                if (result == null)
                {
                    throw new ArgumentNullException("result");
                }

                TAsyncResult asyncResult = result as TAsyncResult;

                if (asyncResult == null)
                {
                    throw new ArgumentException("Invalid async result.", "result");
                }

                if (asyncResult.endCalled)
                {
                    throw new InvalidOperationException("Async object already ended.");
                }

                asyncResult.endCalled = true;

                if (!asyncResult.isCompleted)
                {
                    asyncResult.AsyncWaitHandle.WaitOne();
                }

                if (asyncResult.manualResetEvent != null)
                {
                    asyncResult.manualResetEvent.Close();
                }

                if (asyncResult.exception != null)
                {
                    throw asyncResult.exception;
                }

                return asyncResult;
            }

            protected void Complete(bool completedSynchronously)
            {
                if (isCompleted)
                {
                    throw new InvalidOperationException("This async result is already completed.");
                }

                this.completedSynchronously = completedSynchronously;

                if (completedSynchronously)
                {
                    this.isCompleted = true;
                }
                else
                {
                    lock (ThisLock)
                    {
                        this.isCompleted = true;
                        if (this.manualResetEvent != null)
                        {
                            this.manualResetEvent.Set();
                        }
                    }
                }

                if (callback != null)
                {
                    callback(this);
                }
            }

            protected void Complete(bool completedSynchronously, Exception exception)
            {
                this.exception = exception;
                Complete(completedSynchronously);
            }
        }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="0c1b7-165">Para hospedar o DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="0c1b7-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="0c1b7-166">Abra o arquivo Program.cs no projeto DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="0c1b7-167">Adicione o seguinte `using` instruções.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-167">Add the following `using` statements.</span></span>

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="0c1b7-168">Dentro de `Main()` método, adicione o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="0c1b7-169">Isso cria uma instância da `DiscoveryProxy` classe.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="0c1b7-170">Em seguida, adicione o código a seguir para adicionar um ponto de extremidade de descoberta e um ponto de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```
    try
              {
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                  discoveryEndpoint.IsSystemEndpoint = false;

                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                  proxyServiceHost.Open();

                  Console.WriteLine("Proxy Service started.");
                  Console.WriteLine();
                  Console.WriteLine("Press <ENTER> to terminate the service.");
                  Console.WriteLine();
                  Console.ReadLine();

                  proxyServiceHost.Close();
              }
              catch (CommunicationException e)
              {
                  Console.WriteLine(e.Message);
              }
              catch (TimeoutException e)
              {
                  Console.WriteLine(e.Message);
              }

              if (proxyServiceHost.State != CommunicationState.Closed)
              {
                  Console.WriteLine("Aborting the service...");
                  proxyServiceHost.Abort();
              }
    ```

 <span data-ttu-id="0c1b7-171">Você concluiu a implementar o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="0c1b7-172">Continue no [como: Implementar um serviço de descoberta que registra com o Proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="0c1b7-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c1b7-173">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c1b7-173">Example</span></span>
 <span data-ttu-id="0c1b7-174">Isso é a listagem completa do código usado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="0c1b7-174">This is the full listing of the code used in this topic.</span></span>

```
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    if (manualResetEvent == null)
                    {
                        manualResetEvent = new ManualResetEvent(isCompleted);
                    }
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0c1b7-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c1b7-175">See also</span></span>

- [<span data-ttu-id="0c1b7-176">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="0c1b7-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="0c1b7-177">Como: Implementar um serviço de descoberta que registra com o Proxy de descoberta</span><span class="sxs-lookup"><span data-stu-id="0c1b7-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="0c1b7-178">Como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço</span><span class="sxs-lookup"><span data-stu-id="0c1b7-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="0c1b7-179">Como: O Proxy de descoberta de teste</span><span class="sxs-lookup"><span data-stu-id="0c1b7-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)