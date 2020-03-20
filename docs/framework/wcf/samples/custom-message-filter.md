---
title: Filtro de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183883"
---
# <a name="custom-message-filter"></a><span data-ttu-id="4e204-102">Filtro de mensagem personalizado</span><span class="sxs-lookup"><span data-stu-id="4e204-102">Custom Message Filter</span></span>
<span data-ttu-id="4e204-103">Esta amostra demonstra como substituir os filtros de mensagem que o Windows Communication Foundation (WCF) usa para enviar mensagens para pontos finais.</span><span class="sxs-lookup"><span data-stu-id="4e204-103">This sample demonstrates how to replace the message filters that Windows Communication Foundation (WCF) uses to dispatch messages to endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e204-104">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4e204-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4e204-105">Quando a primeira mensagem em um canal chega ao servidor, o servidor deve determinar qual (se houver) dos pontos finais associados a esse URI deve receber a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4e204-105">When the first message on a channel arrives at the server, the server must determine which (if any) of the endpoints associated with that URI should receive the message.</span></span> <span data-ttu-id="4e204-106">Este processo é <xref:System.ServiceModel.Dispatcher.MessageFilter> controlado pelos objetos ligados ao <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span><span class="sxs-lookup"><span data-stu-id="4e204-106">This process is controlled by the <xref:System.ServiceModel.Dispatcher.MessageFilter> objects attached to the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span>  
  
 <span data-ttu-id="4e204-107">Cada ponto final de um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>serviço tem um único .</span><span class="sxs-lookup"><span data-stu-id="4e204-107">Each endpoint of a service has a single <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.</span></span> <span data-ttu-id="4e204-108">O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> tem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>e um .</span><span class="sxs-lookup"><span data-stu-id="4e204-108">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> has both an <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>.</span></span> <span data-ttu-id="4e204-109">A união desses dois filtros é o filtro de mensagem usado para esse ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e204-109">The union of these two filters is the message filter used for that endpoint.</span></span>  
  
 <span data-ttu-id="4e204-110">Por padrão, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> o ponto final corresponde a qualquer mensagem endereçada a <xref:System.ServiceModel.EndpointAddress>um endereço que corresponda ao ponto final do serviço .</span><span class="sxs-lookup"><span data-stu-id="4e204-110">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> for an endpoint matches any message that is addressed to an address that matches the service endpoint's <xref:System.ServiceModel.EndpointAddress>.</span></span> <span data-ttu-id="4e204-111">Por padrão, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> o ponto final inspeciona a ação da mensagem recebida e corresponde a qualquer mensagem com uma ação que `IsInitiating` = `true` corresponda a uma das ações das operações do contrato de ponto final do serviço (apenas ações são consideradas).</span><span class="sxs-lookup"><span data-stu-id="4e204-111">By default, the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> for an endpoint inspects the action of the incoming message and matches any message with an action that corresponds to one of the actions of the service endpoint contract's operations (only `IsInitiating`=`true` actions are considered).</span></span> <span data-ttu-id="4e204-112">Como resultado, por padrão, o filtro para um ponto final só corresponde <xref:System.ServiceModel.EndpointAddress> se o cabeçalho da mensagem for o ponto final e a ação da mensagem corresponder a uma das ações da operação de ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e204-112">As a result, by default, the filter for an endpoint only matches if both the message's To header is the <xref:System.ServiceModel.EndpointAddress> of the endpoint and the message's action matches one of the endpoint operation's actions.</span></span>  
  
 <span data-ttu-id="4e204-113">Esses filtros podem ser alterados usando um comportamento.</span><span class="sxs-lookup"><span data-stu-id="4e204-113">These filters can be changed using a behavior.</span></span> <span data-ttu-id="4e204-114">Na amostra, o serviço <xref:System.ServiceModel.Description.IEndpointBehavior> cria um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> que <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>substitui o e sobre o :</span><span class="sxs-lookup"><span data-stu-id="4e204-114">In the sample, the service creates an <xref:System.ServiceModel.Description.IEndpointBehavior> that replaces the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> and <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> on the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:</span></span>  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 <span data-ttu-id="4e204-115">Dois filtros de endereço são definidos:</span><span class="sxs-lookup"><span data-stu-id="4e204-115">Two address filters are defined:</span></span>  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 <span data-ttu-id="4e204-116">O `FilteringEndpointBehavior` é configurável e permite duas variações diferentes.</span><span class="sxs-lookup"><span data-stu-id="4e204-116">The `FilteringEndpointBehavior` is made configurable and allows for two different variations.</span></span>  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 <span data-ttu-id="4e204-117">A variação 1 corresponde apenas aos endereços que contenham um 'e' (mas que tenham qualquer Ação), enquanto a Variação 2 corresponde apenas aos endereços que não possuem um 'e':</span><span class="sxs-lookup"><span data-stu-id="4e204-117">Variation 1 matches only addresses that contain an 'e' (but that have any Action) whereas Variation 2 matches only addresses that lack an 'e':</span></span>  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 <span data-ttu-id="4e204-118">No arquivo de configuração, o serviço registra o novo comportamento:</span><span class="sxs-lookup"><span data-stu-id="4e204-118">In the configuration file, the service registers the new behavior:</span></span>  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 <span data-ttu-id="4e204-119">Em seguida, `endpointBehavior` o serviço cria configurações para cada variação:</span><span class="sxs-lookup"><span data-stu-id="4e204-119">Then the service creates `endpointBehavior` configurations for each variation:</span></span>  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 <span data-ttu-id="4e204-120">Finalmente, o ponto final do serviço `behaviorConfigurations`faz referência a um dos:</span><span class="sxs-lookup"><span data-stu-id="4e204-120">Finally, the service's endpoint references one of the `behaviorConfigurations`:</span></span>  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 <span data-ttu-id="4e204-121">A implementação do aplicativo cliente é simples; ele cria dois canais para o URI do serviço (passando`via`esse valor <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> como o segundo parâmetro ( ) para e envia uma única mensagem em cada canal, mas usa endereços de ponto final diferentes para cada um.</span><span class="sxs-lookup"><span data-stu-id="4e204-121">The implementation of the client application is straightforward; it creates two channels to the service's URI (by passing in that value as the second (`via`) parameter to <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> and sends a single message on each channel, but it uses different endpoint addresses for each.</span></span> <span data-ttu-id="4e204-122">Como resultado, as mensagens de saída do cliente têm designações diferentes para, e o servidor responde de acordo, como demonstrado pela saída do cliente:</span><span class="sxs-lookup"><span data-stu-id="4e204-122">As a result, the outbound messages from the client have different To designations, and the server responds accordingly, as demonstrated by the client's output:</span></span>  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 <span data-ttu-id="4e204-123">A mudança no arquivo de configuração do servidor faz com que o filtro seja trocado e o cliente veja o comportamento oposto (a mensagem é `urn:e` bem sucedida, enquanto a mensagem falha). `urn:a`</span><span class="sxs-lookup"><span data-stu-id="4e204-123">Switching the variation in the server's configuration file causes the filter to be swapped and the client sees the opposite behavior (the message to `urn:e` succeeds, whereas the message to `urn:a` fails).</span></span>  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="4e204-124">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4e204-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e204-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4e204-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4e204-126">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="4e204-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e204-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4e204-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e204-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4e204-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e204-129">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e204-129">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="4e204-130">Para executar a amostra em uma configuração de uma única máquina, siga as instruções em [Executar as amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e204-130">To run the sample in a single-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4e204-131">Para executar a amostra em uma configuração entre máquinas, siga as instruções em [Executar a Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) e altere a seguinte linha em Client.cs.</span><span class="sxs-lookup"><span data-stu-id="4e204-131">To run the sample in a cross-machine configuration, follow the instructions at [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) and change the following line in Client.cs.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     <span data-ttu-id="4e204-132">Substitua o host local pelo nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="4e204-132">Replace localhost with the name of server.</span></span>  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
