---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: af925a0f16e59cb6fec3ec246bd64a8f109d4d57
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270313"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="dceb5-101">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="dceb5-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="dceb5-102">Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP multicast de associação.</span><span class="sxs-lookup"><span data-stu-id="dceb5-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="dceb5-103">Esse ponto de extremidade tem um contrato fixo e oferece suporte a duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="dceb5-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="dceb5-104">Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="dceb5-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
 <span data-ttu-id="dceb5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dceb5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="dceb5-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dceb5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dceb5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dceb5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dceb5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dceb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dceb5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dceb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dceb5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="dceb5-110">Attributes</span></span>  
  
|<span data-ttu-id="dceb5-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="dceb5-111">Attribute</span></span>|<span data-ttu-id="dceb5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dceb5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dceb5-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="dceb5-113">discoveryMode</span></span>|<span data-ttu-id="dceb5-114">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dceb5-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="dceb5-115">Os valores válidos são "Adhoc" e "Gerenciado".</span><span class="sxs-lookup"><span data-stu-id="dceb5-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="dceb5-116">No modo gerenciado o protocolo se baseia em um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="dceb5-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="dceb5-117">Modo ad hoc requer o protocolo a usar o UDP multicast mecanismo para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dceb5-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="dceb5-118">Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="dceb5-118">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="dceb5-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="dceb5-119">discoveryVersion</span></span>|<span data-ttu-id="dceb5-120">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="dceb5-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="dceb5-121">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="dceb5-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="dceb5-122">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="dceb5-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="dceb5-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="dceb5-123">maxResponseDelay</span></span>|<span data-ttu-id="dceb5-124">Um valor de Timespan que especifica o valor máximo para o atraso, o protocolo de descoberta irá esperar antes de enviar determinadas mensagens, como correspondência de investigação ou resolver.</span><span class="sxs-lookup"><span data-stu-id="dceb5-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="dceb5-125">Se todas as ProbeMatches forem enviadas ao mesmo tempo, pode resultar uma tempestade de rede.</span><span class="sxs-lookup"><span data-stu-id="dceb5-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="dceb5-126">Para evitar que isso ocorra, ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="dceb5-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="dceb5-127">É o atraso aleatório no intervalo de 0 até o valor definido por este atributo.</span><span class="sxs-lookup"><span data-stu-id="dceb5-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="dceb5-128">Se esse atributo é definido como 0, as ProbeMatches de mensagens são enviadas em um loop estreito sem demora.</span><span class="sxs-lookup"><span data-stu-id="dceb5-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="dceb5-129">Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total decorrido para enviar mensagens de todas as ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="dceb5-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="dceb5-130">Esse valor só é relevante para os serviços, ele não é usado pelos clientes.</span><span class="sxs-lookup"><span data-stu-id="dceb5-130">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="dceb5-131">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="dceb5-131">multicastAddress</span></span>|<span data-ttu-id="dceb5-132">Um Uri que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="dceb5-132">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="dceb5-133">O valor padrão é o endereço multicast como em conformidade com a especificação do protocolo.</span><span class="sxs-lookup"><span data-stu-id="dceb5-133">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="dceb5-134">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="dceb5-134">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="dceb5-135">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="dceb5-135">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dceb5-136">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dceb5-136">Child Elements</span></span>  
  
|<span data-ttu-id="dceb5-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="dceb5-137">Element</span></span>|<span data-ttu-id="dceb5-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="dceb5-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dceb5-139">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="dceb5-139">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="dceb5-140">Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="dceb5-140">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dceb5-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dceb5-141">Parent Elements</span></span>  
  
|<span data-ttu-id="dceb5-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="dceb5-142">Element</span></span>|<span data-ttu-id="dceb5-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="dceb5-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dceb5-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dceb5-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="dceb5-145">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="dceb5-145">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dceb5-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dceb5-146">Example</span></span>  
 <span data-ttu-id="dceb5-147">O exemplo a seguir demonstra um serviço de escuta para mensagens de descoberta através de um UDP multicast de transporte.</span><span class="sxs-lookup"><span data-stu-id="dceb5-147">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dceb5-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dceb5-148">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
