---
title: Balanceamento de Carga
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183987"
---
# <a name="load-balancing"></a><span data-ttu-id="386ad-102">Balanceamento de Carga</span><span class="sxs-lookup"><span data-stu-id="386ad-102">Load Balancing</span></span>
<span data-ttu-id="386ad-103">Uma maneira de aumentar a capacidade dos aplicativos do Windows Communication Foundation (WCF) é dimensioná-los implantando-os em uma fazenda de servidores equilibrada de carga.</span><span class="sxs-lookup"><span data-stu-id="386ad-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="386ad-104">Os aplicativos WCF podem ser balanceados de carga usando técnicas padrão de balanceamento de carga, incluindo balanceadores de carga de software, como o Balanceamento de Carga de Rede do Windows, bem como aparelhos de balanceamento de carga baseados em hardware.</span><span class="sxs-lookup"><span data-stu-id="386ad-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="386ad-105">As seções a seguir discutem considerações para o balanceamento de carga de aplicativos WCF construídos usando várias vinculações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="386ad-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="386ad-106">Balanceamento de carga com a vinculação http básica</span><span class="sxs-lookup"><span data-stu-id="386ad-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="386ad-107">Do ponto de vista do balanceamento de carga, os aplicativos WCF que se comunicam usando o <xref:System.ServiceModel.BasicHttpBinding> não são diferentes de outros tipos comuns de tráfego de rede HTTP (conteúdo HTML estático, páginas ASP.NET ou Serviços Web ASMX).</span><span class="sxs-lookup"><span data-stu-id="386ad-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="386ad-108">Os canais WCF que usam essa vinculação são inerentemente apátridas e terminam suas conexões quando o canal fecha.</span><span class="sxs-lookup"><span data-stu-id="386ad-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="386ad-109">Como tal, <xref:System.ServiceModel.BasicHttpBinding> o funciona bem com as técnicas de balanceamento de carga HTTP existentes.</span><span class="sxs-lookup"><span data-stu-id="386ad-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="386ad-110">Por padrão, <xref:System.ServiceModel.BasicHttpBinding> o envia um cabeçalho `Keep-Alive` HTTP de conexão em mensagens com um valor, o que permite que os clientes estabeleçam conexões persistentes aos serviços que os suportam.</span><span class="sxs-lookup"><span data-stu-id="386ad-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="386ad-111">Essa configuração oferece throughput aprimorado porque conexões previamente estabelecidas podem ser reutilizadas para enviar mensagens subseqüentes para o mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="386ad-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="386ad-112">No entanto, a reutilização de conexão pode fazer com que os clientes se tornem fortemente associados a um servidor específico dentro da fazenda balanceada de carga, o que reduz a eficácia do balanceamento de carga de round-robin.</span><span class="sxs-lookup"><span data-stu-id="386ad-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="386ad-113">Se esse comportamento for `Keep-Alive` indesejável, http pode <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> ser desativado <xref:System.ServiceModel.Channels.CustomBinding> no servidor <xref:System.ServiceModel.Channels.Binding>usando a propriedade com um ou definido pelo usuário .</span><span class="sxs-lookup"><span data-stu-id="386ad-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="386ad-114">O exemplo a seguir mostra como fazer isso usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="386ad-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="386ad-115">Usando a configuração simplificada introduzida no .NET Framework 4, o mesmo comportamento pode ser realizado usando a seguinte configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="386ad-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="386ad-116">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](simplified-configuration.md) e [Configuração simplificada para serviços WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="386ad-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="386ad-117">Balanceamento de carga com a vinculação WSHttp e a vinculação WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="386ad-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="386ad-118">Tanto <xref:System.ServiceModel.WSHttpBinding> o <xref:System.ServiceModel.WSDualHttpBinding> e o pode ser carregado balanceado usando técnicas de balanceamento de carga HTTP, desde que várias modificações sejam feitas na configuração de vinculação padrão.</span><span class="sxs-lookup"><span data-stu-id="386ad-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="386ad-119">Desativar o Estabelecimento de Contexto de Segurança: <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> isso <xref:System.ServiceModel.WSHttpBinding> pode `false`ser realizado pela configuração da propriedade no para .</span><span class="sxs-lookup"><span data-stu-id="386ad-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="386ad-120">Alternativamente, se as sessões de segurança forem necessárias, é possível usar sessões de segurança estaduais conforme descrito no tópico [Sessões Seguras.](./feature-details/secure-sessions.md)</span><span class="sxs-lookup"><span data-stu-id="386ad-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="386ad-121">As sessões de segurança estaduais permitem que o serviço permaneça apátrida, pois todo o estado para a sessão de segurança é transmitido a cada solicitação como parte do token de segurança de proteção.</span><span class="sxs-lookup"><span data-stu-id="386ad-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="386ad-122">Observe que para habilitar uma sessão de segurança <xref:System.ServiceModel.Channels.CustomBinding> de estado, é necessário usar uma ou definida configuração necessária, <xref:System.ServiceModel.Channels.Binding> pois as configurações necessárias não estão expostas <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.WSDualHttpBinding> que são fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="386ad-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="386ad-123">Não use sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="386ad-123">Do not use reliable sessions.</span></span> <span data-ttu-id="386ad-124">Esse recurso está desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="386ad-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="386ad-125">Balanceamento de carga da vinculação Net.TCP</span><span class="sxs-lookup"><span data-stu-id="386ad-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="386ad-126">A <xref:System.ServiceModel.NetTcpBinding> carga pode ser balanceada usando técnicas de balanceamento de carga de camada IP.</span><span class="sxs-lookup"><span data-stu-id="386ad-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="386ad-127">No entanto, os <xref:System.ServiceModel.NetTcpBinding> pools de conexões TCP por padrão para reduzir a latência de conexão.</span><span class="sxs-lookup"><span data-stu-id="386ad-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="386ad-128">Trata-se de uma otimização que interfere no mecanismo básico de balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="386ad-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="386ad-129">O principal valor de <xref:System.ServiceModel.NetTcpBinding> configuração para otimizar o é o tempo de locação, que faz parte das Configurações do Pool de Conexões.</span><span class="sxs-lookup"><span data-stu-id="386ad-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="386ad-130">O pool de conexões faz com que as conexões com clientes se tornem associadas a servidores específicos dentro da fazenda.</span><span class="sxs-lookup"><span data-stu-id="386ad-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="386ad-131">À medida que a vida útil dessas conexões aumenta (um fator controlado pela configuração do tempo limite de locação), a distribuição de carga entre vários servidores da fazenda torna-se desequilibrada.</span><span class="sxs-lookup"><span data-stu-id="386ad-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="386ad-132">Como resultado, o tempo médio de chamada aumenta.</span><span class="sxs-lookup"><span data-stu-id="386ad-132">As a result the average call time increases.</span></span> <span data-ttu-id="386ad-133">Portanto, ao <xref:System.ServiceModel.NetTcpBinding> usar os cenários em equilíbrio de carga, considere reduzir o tempo de locação padrão usado pela vinculação.</span><span class="sxs-lookup"><span data-stu-id="386ad-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="386ad-134">Um tempo de locação de 30 segundos é um ponto de partida razoável para cenários equilibrados de carga, embora o valor ideal seja dependente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="386ad-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="386ad-135">Para obter mais informações sobre o tempo de tempo de locação do canal e outras cotas de transporte, consulte [Cotas de Transporte](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="386ad-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="386ad-136">Para obter o melhor desempenho em <xref:System.ServiceModel.NetTcpSecurity> cenários <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>equilibrados de carga, considere usar (ou ).</span><span class="sxs-lookup"><span data-stu-id="386ad-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386ad-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="386ad-137">See also</span></span>

- [<span data-ttu-id="386ad-138">Práticas recomendadas de hospedagem de Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="386ad-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
