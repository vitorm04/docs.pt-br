---
title: Balanceamento de carga
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 572537826074dd51b56f1cae9edb767708bc1c3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321029"
---
# <a name="load-balancing"></a><span data-ttu-id="b7922-102">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="b7922-102">Load Balancing</span></span>
<span data-ttu-id="b7922-103">Uma maneira de aumentar a capacidade dos aplicativos de Windows Communication Foundation (WCF) é expandi-los implantando-os em um farm de servidores com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="b7922-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="b7922-104">Os aplicativos WCF podem ter balanceamento de carga usando técnicas de balanceamento de carga padrão, incluindo balanceadores de carga de software, como balanceamento de carga de rede do Windows, bem como dispositivos de balanceamento de carga baseados em hardware.</span><span class="sxs-lookup"><span data-stu-id="b7922-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="b7922-105">As seções a seguir discutem considerações sobre o balanceamento de carga de aplicativos WCF criados usando várias associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="b7922-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="b7922-106">Balanceamento de carga com a associação HTTP básica</span><span class="sxs-lookup"><span data-stu-id="b7922-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="b7922-107">Da perspectiva do balanceamento de carga, os aplicativos WCF que se comunicam usando o <xref:System.ServiceModel.BasicHttpBinding> não são diferentes dos outros tipos comuns de tráfego de rede HTTP (conteúdo HTML estático, páginas ASP.NET ou Web Services ASMX).</span><span class="sxs-lookup"><span data-stu-id="b7922-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="b7922-108">Os canais do WCF que usam essa associação são inerentemente sem monitoração de estado e encerram suas conexões quando o canal é fechado.</span><span class="sxs-lookup"><span data-stu-id="b7922-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="b7922-109">Assim, o <xref:System.ServiceModel.BasicHttpBinding> funciona bem com as técnicas de balanceamento de carga HTTP existentes.</span><span class="sxs-lookup"><span data-stu-id="b7922-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="b7922-110">Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> envia um cabeçalho HTTP de conexão em mensagens com um valor de `Keep-Alive`, que permite que os clientes estabeleçam conexões persistentes com os serviços que dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="b7922-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="b7922-111">Essa configuração oferece uma taxa de transferência avançada porque as conexões estabelecidas anteriormente podem ser reutilizadas para enviar mensagens subsequentes para o mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="b7922-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="b7922-112">No entanto, a reutilização de conexão pode fazer com que os clientes se tornem fortemente associados a um servidor específico dentro do farm com balanceamento de carga, o que reduz a eficácia do balanceamento de carga Round Robin.</span><span class="sxs-lookup"><span data-stu-id="b7922-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="b7922-113">Se esse comportamento for indesejável, o HTTP `Keep-Alive` poderá ser desabilitado no servidor usando a propriedade <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> com um <xref:System.ServiceModel.Channels.CustomBinding> ou definido pelo usuário <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b7922-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b7922-114">O exemplo a seguir mostra como fazer isso usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="b7922-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b7922-115">Usando a configuração simplificada introduzida no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], o mesmo comportamento pode ser feito usando a seguinte configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="b7922-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b7922-116">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b7922-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="b7922-117">Balanceamento de carga com a associação WSHttp e a associação WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="b7922-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="b7922-118">O <xref:System.ServiceModel.WSHttpBinding> e o <xref:System.ServiceModel.WSDualHttpBinding> podem ter balanceamento de carga usando técnicas de balanceamento de carga HTTP, desde que várias modificações sejam feitas na configuração de associação padrão.</span><span class="sxs-lookup"><span data-stu-id="b7922-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="b7922-119">Desativar o estabelecimento do contexto de segurança: isso pode ser feito pela configuração da propriedade <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> no <xref:System.ServiceModel.WSHttpBinding> para `false`.</span><span class="sxs-lookup"><span data-stu-id="b7922-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="b7922-120">Como alternativa, se as sessões de segurança forem necessárias, será possível usar sessões de segurança com estado conforme descrito no tópico [sessões seguras](./feature-details/secure-sessions.md) .</span><span class="sxs-lookup"><span data-stu-id="b7922-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="b7922-121">As sessões de segurança com estado permitem que o serviço permaneça sem estado, pois todo o estado da sessão de segurança é transmitido com cada solicitação como parte do token de segurança de proteção.</span><span class="sxs-lookup"><span data-stu-id="b7922-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="b7922-122">Observe que para habilitar uma sessão de segurança com estado, é necessário usar um <xref:System.ServiceModel.Channels.CustomBinding> ou <xref:System.ServiceModel.Channels.Binding> definido pelo usuário, já que as definições de configuração necessárias não são expostas em <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> fornecidos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="b7922-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="b7922-123">Não use sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="b7922-123">Do not use reliable sessions.</span></span> <span data-ttu-id="b7922-124">Esse recurso está desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="b7922-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="b7922-125">Balanceamento de carga da Associação net. TCP</span><span class="sxs-lookup"><span data-stu-id="b7922-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="b7922-126">O <xref:System.ServiceModel.NetTcpBinding> pode ter balanceamento de carga usando técnicas de balanceamento de carga de camada de IP.</span><span class="sxs-lookup"><span data-stu-id="b7922-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="b7922-127">No entanto, as conexões TCP de pools <xref:System.ServiceModel.NetTcpBinding> por padrão reduzem a latência de conexão.</span><span class="sxs-lookup"><span data-stu-id="b7922-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="b7922-128">Essa é uma otimização que interfere no mecanismo básico de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="b7922-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="b7922-129">O valor de configuração principal para otimizar o <xref:System.ServiceModel.NetTcpBinding> é o tempo limite de concessão, que faz parte das configurações do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="b7922-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="b7922-130">O pooling de conexões faz com que as conexões de cliente se tornem associadas a servidores específicos no farm.</span><span class="sxs-lookup"><span data-stu-id="b7922-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="b7922-131">À medida que a vida útil dessas conexões aumenta (um fator controlado pela configuração de tempo limite de concessão), a distribuição de carga entre vários servidores no farm torna-se desbalanceada.</span><span class="sxs-lookup"><span data-stu-id="b7922-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="b7922-132">Como resultado, o tempo médio de chamada aumenta.</span><span class="sxs-lookup"><span data-stu-id="b7922-132">As a result the average call time increases.</span></span> <span data-ttu-id="b7922-133">Portanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> em cenários com balanceamento de carga, considere reduzir o tempo limite de concessão padrão usado pela associação.</span><span class="sxs-lookup"><span data-stu-id="b7922-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="b7922-134">Um tempo limite de concessão de 30 segundos é um ponto de partida razoável para cenários com balanceamento de carga, embora o valor ideal seja dependente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7922-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="b7922-135">Para obter mais informações sobre o tempo limite de concessão de canal e outras cotas de transporte, consulte [cotas de transporte](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="b7922-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="b7922-136">Para obter o melhor desempenho em cenários com balanceamento de carga, considere o uso de <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> ou <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="b7922-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7922-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7922-137">See also</span></span>

- [<span data-ttu-id="b7922-138">Práticas recomendadas de hospedagem de Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="b7922-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
