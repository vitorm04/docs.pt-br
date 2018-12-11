---
title: '&lt;UdpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 01808594d54d5c79a6530bc7f6a03b66dde7ee99
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144748"
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="68dd6-102">&lt;UdpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="68dd6-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="68dd6-103">Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP multicast de associação.</span><span class="sxs-lookup"><span data-stu-id="68dd6-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="68dd6-104">Esse ponto de extremidade tem um contrato fixo e oferece suporte a duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="68dd6-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="68dd6-105">Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="68dd6-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="68dd6-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68dd6-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="68dd6-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="68dd6-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68dd6-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68dd6-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68dd6-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68dd6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="68dd6-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68dd6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68dd6-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="68dd6-111">Attributes</span></span>  
  
|<span data-ttu-id="68dd6-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="68dd6-112">Attribute</span></span>|<span data-ttu-id="68dd6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="68dd6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68dd6-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="68dd6-114">discoveryMode</span></span>|<span data-ttu-id="68dd6-115">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="68dd6-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="68dd6-116">Os valores válidos são "Adhoc" e "Gerenciado".</span><span class="sxs-lookup"><span data-stu-id="68dd6-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="68dd6-117">No modo gerenciado o protocolo se baseia em um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="68dd6-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="68dd6-118">Modo ad hoc requer o protocolo a usar o UDP multicast mecanismo para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="68dd6-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="68dd6-119">Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="68dd6-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="68dd6-120">DiscoveryVersion</span><span class="sxs-lookup"><span data-stu-id="68dd6-120">discoveryVersion</span></span>|<span data-ttu-id="68dd6-121">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="68dd6-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="68dd6-122">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="68dd6-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="68dd6-123">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="68dd6-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="68dd6-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="68dd6-124">maxResponseDelay</span></span>|<span data-ttu-id="68dd6-125">Um valor de Timespan que especifica o valor máximo para o atraso, o protocolo de descoberta irá esperar antes de enviar determinadas mensagens, como correspondência de investigação ou resolver.</span><span class="sxs-lookup"><span data-stu-id="68dd6-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="68dd6-126">Se todas as ProbeMatches forem enviadas ao mesmo tempo, pode resultar uma tempestade de rede.</span><span class="sxs-lookup"><span data-stu-id="68dd6-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="68dd6-127">Para evitar que isso ocorra, ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="68dd6-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="68dd6-128">É o atraso aleatório no intervalo de 0 até o valor definido por este atributo.</span><span class="sxs-lookup"><span data-stu-id="68dd6-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="68dd6-129">Se esse atributo é definido como 0, as ProbeMatches de mensagens são enviadas em um loop estreito sem demora.</span><span class="sxs-lookup"><span data-stu-id="68dd6-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="68dd6-130">Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total decorrido para enviar mensagens de todas as ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="68dd6-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="68dd6-131">Esse valor só é relevante para os serviços, ele não é usado pelos clientes.</span><span class="sxs-lookup"><span data-stu-id="68dd6-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="68dd6-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="68dd6-132">multicastAddress</span></span>|<span data-ttu-id="68dd6-133">Um Uri que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="68dd6-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="68dd6-134">O valor padrão é o endereço multicast como em conformidade com a especificação do protocolo.</span><span class="sxs-lookup"><span data-stu-id="68dd6-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="68dd6-135">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="68dd6-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="68dd6-136">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="68dd6-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68dd6-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68dd6-137">Child Elements</span></span>  
  
|<span data-ttu-id="68dd6-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="68dd6-138">Element</span></span>|<span data-ttu-id="68dd6-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="68dd6-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68dd6-140">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="68dd6-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="68dd6-141">Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="68dd6-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68dd6-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68dd6-142">Parent Elements</span></span>  
  
|<span data-ttu-id="68dd6-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="68dd6-143">Element</span></span>|<span data-ttu-id="68dd6-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="68dd6-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68dd6-145">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="68dd6-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="68dd6-146">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="68dd6-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68dd6-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68dd6-147">Example</span></span>  
 <span data-ttu-id="68dd6-148">O exemplo a seguir demonstra um serviço de escuta para mensagens de descoberta através de um UDP multicast de transporte.</span><span class="sxs-lookup"><span data-stu-id="68dd6-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <endpoint binding="basicHttpBinding"   
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="DiscoveryEndpoint"  
              kind="udpDiscoveryEndpoint" />  
  </service>  
  <standardEndpoints>  
    <udpDiscoveryEndpoint>  
      <standardEndpoint name="DiscoveryEndpoint"                         
                        version="WSDiscoveryApril2005" />  
    </udpDiscoveryEndpoint>  
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="68dd6-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68dd6-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
