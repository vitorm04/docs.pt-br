---
title: Usando o NetHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba5c8a977513ebaae902e3c3d37f950003548474
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="91bf7-102">Usando o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="91bf7-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="91bf7-103">O <xref:System.ServiceModel.NetHttpBinding> é uma associação criada para consumir HTTP ou serviços WebSocket e usa a codificação binária por padrão.</span><span class="sxs-lookup"><span data-stu-id="91bf7-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="91bf7-104">O <xref:System.ServiceModel.NetHttpBinding> detectará se tiver sido usado com contrato de solicitação-resposta ou contrato de duplex e alterará seu comportamento para corresponder. Ele usará HTTP para contratos de solicitação-resposta e WebSockets para contratos duplex.</span><span class="sxs-lookup"><span data-stu-id="91bf7-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="91bf7-105">Esse comportamento pode ser substituído usando o <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` configuração:</span><span class="sxs-lookup"><span data-stu-id="91bf7-105">This behavior can be overridden using the <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` setting:</span></span>  
  
1.  <span data-ttu-id="91bf7-106">Sempre - isso força o WebSockets a ser usado mesmo para contratos de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="91bf7-106">Always - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2.  <span data-ttu-id="91bf7-107">Nunca - isso impede que o WebSockets seja usado.</span><span class="sxs-lookup"><span data-stu-id="91bf7-107">Never - This prevents WebSockets from being used.</span></span> <span data-ttu-id="91bf7-108">Tentar usar um contrato duplex com esta configuração resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="91bf7-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3.  <span data-ttu-id="91bf7-109">WhenDuplex - este é o valor padrão e comporta-se como descrito acima.</span><span class="sxs-lookup"><span data-stu-id="91bf7-109">WhenDuplex - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="91bf7-110">O <xref:System.ServiceModel.NetHttpBinding> oferece suporte a sessões confiáveis no modo HTTP e no modo WebSocket.</span><span class="sxs-lookup"><span data-stu-id="91bf7-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="91bf7-111">No modo WebSocket as sessões são fornecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="91bf7-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="91bf7-112">Quando usar o <xref:System.ServiceModel.NetHttpBinding> e o TransferMode da associação estiver definido como TransferMode.Streamed, os fluxos grandes podem causar um deadlock e a chamada atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="91bf7-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="91bf7-113">Para solucionar esse problema, envie mensagens menores ou use TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="91bf7-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="91bf7-114">Configurando um serviço para usar NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="91bf7-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="91bf7-115">O <xref:System.ServiceModel.NetHttpBinding> pode ser configurado da mesma maneira que qualquer outra associação.</span><span class="sxs-lookup"><span data-stu-id="91bf7-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="91bf7-116">O trecho da configuração a seguir demonstra como configurar um serviço WCF com <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="91bf7-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 <span data-ttu-id="91bf7-117">O trecho de código a seguir mostra como adicionar o <xref:System.ServiceModel.NetHttpBinding> no código.</span><span class="sxs-lookup"><span data-stu-id="91bf7-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="91bf7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91bf7-118">See Also</span></span>  
 <span data-ttu-id="91bf7-119">[Configuring Bindings for Services](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md) (Configurando associações para serviços)</span><span class="sxs-lookup"><span data-stu-id="91bf7-119">[Configuring Bindings for Services](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)</span></span>  
 <span data-ttu-id="91bf7-120">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="91bf7-120">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md)</span></span>  
 <span data-ttu-id="91bf7-121">[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md) (Associações fornecidas pelo sistema)</span><span class="sxs-lookup"><span data-stu-id="91bf7-121">[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)</span></span>  
 [<span data-ttu-id="91bf7-122">Serviços duplex</span><span class="sxs-lookup"><span data-stu-id="91bf7-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
