---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 1729255c68c75f824b8cd8c87f106a4a9b3550f6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854884"
---
# <a name="udpdiscoveryendpoint"></a><span data-ttu-id="8f5ec-101">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="8f5ec-101">\<udpDiscoveryEndpoint></span></span>
<span data-ttu-id="8f5ec-102">Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta em uma associação de multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="8f5ec-103">Esse ponto de extremidade tem um contrato fixo e dá suporte a duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="8f5ec-104">Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="8f5ec-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
<span data-ttu-id="8f5ec-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f5ec-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f5ec-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f5ec-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f5ec-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="8f5ec-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="8f5ec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> udpDiscoveryEndpoint**</span><span class="sxs-lookup"><span data-stu-id="8f5ec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5ec-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f5ec-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f5ec-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f5ec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8f5ec-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f5ec-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f5ec-112">Attributes</span></span>  
  
|<span data-ttu-id="8f5ec-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f5ec-113">Attribute</span></span>|<span data-ttu-id="8f5ec-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5ec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f5ec-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="8f5ec-115">discoveryMode</span></span>|<span data-ttu-id="8f5ec-116">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="8f5ec-117">Os valores válidos são "adhoc" e "Managed".</span><span class="sxs-lookup"><span data-stu-id="8f5ec-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="8f5ec-118">No modo gerenciado, o protocolo depende de um proxy de descoberta, que atua como um repositório de serviços detectáveis.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="8f5ec-119">O modo adhoc requer que o protocolo use o mecanismo de multicast UDP para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="8f5ec-120">Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-120">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="8f5ec-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="8f5ec-121">discoveryVersion</span></span>|<span data-ttu-id="8f5ec-122">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="8f5ec-123">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="8f5ec-124">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="8f5ec-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="8f5ec-125">maxResponseDelay</span></span>|<span data-ttu-id="8f5ec-126">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar determinadas mensagens, como correspondência de investigação ou resolução de correspondência.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="8f5ec-127">Se todos os ProbeMatches forem enviados ao mesmo tempo, um Storm de rede poderá resultar.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="8f5ec-128">Para evitar que isso ocorra, os ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="8f5ec-129">O atraso aleatório está no intervalo de 0 até o valor definido por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="8f5ec-130">Se esse atributo for definido como 0, as mensagens ProbeMatches serão enviadas em um loop rígido sem nenhum atraso.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="8f5ec-131">Caso contrário, as mensagens ProbeMatches são enviadas com um atraso aleatório, de modo que o tempo total necessário para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="8f5ec-132">Esse valor só é relevante para os serviços, não é usado por clientes.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-132">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="8f5ec-133">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="8f5ec-133">multicastAddress</span></span>|<span data-ttu-id="8f5ec-134">Um URI que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-134">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="8f5ec-135">O valor padrão é o endereço de multicast como compatível com a especificação de protocolo.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-135">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="8f5ec-136">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-136">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="8f5ec-137">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-137">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f5ec-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f5ec-138">Child Elements</span></span>  
  
|<span data-ttu-id="8f5ec-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f5ec-139">Element</span></span>|<span data-ttu-id="8f5ec-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5ec-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f5ec-141">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="8f5ec-141">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="8f5ec-142">Uma coleção de configurações que permitem configurar o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-142">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f5ec-143">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f5ec-143">Parent Elements</span></span>  
  
|<span data-ttu-id="8f5ec-144">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f5ec-144">Element</span></span>|<span data-ttu-id="8f5ec-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5ec-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f5ec-146">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8f5ec-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8f5ec-147">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-147">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f5ec-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f5ec-148">Example</span></span>  
 <span data-ttu-id="8f5ec-149">O exemplo a seguir demonstra um serviço de escuta de mensagens de descoberta em um transporte multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="8f5ec-149">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f5ec-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f5ec-150">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
