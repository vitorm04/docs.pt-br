---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855400"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="92b5a-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="92b5a-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="92b5a-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato de descoberta fixo.</span><span class="sxs-lookup"><span data-stu-id="92b5a-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="92b5a-103">Quando adicionado à configuração de serviço, ele especifica onde ouvir as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="92b5a-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="92b5a-104">Quando adicionado à configuração do cliente, ele especifica para onde enviar as consultas de descoberta.</span><span class="sxs-lookup"><span data-stu-id="92b5a-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="92b5a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="92b5a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="92b5a-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="92b5a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="92b5a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="92b5a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="92b5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> discoveryEndpoint**</span><span class="sxs-lookup"><span data-stu-id="92b5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b5a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92b5a-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92b5a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="92b5a-110">Attributes and elements</span></span>

<span data-ttu-id="92b5a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="92b5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92b5a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="92b5a-112">Attributes</span></span>

| <span data-ttu-id="92b5a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="92b5a-113">Attribute</span></span>        | <span data-ttu-id="92b5a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="92b5a-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="92b5a-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="92b5a-115">discoveryMode</span></span>    | <span data-ttu-id="92b5a-116">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="92b5a-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="92b5a-117">Os valores válidos são "adhoc" e "Managed".</span><span class="sxs-lookup"><span data-stu-id="92b5a-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="92b5a-118">No modo gerenciado, o protocolo depende de um proxy de descoberta, que atua como um repositório de serviços detectáveis.</span><span class="sxs-lookup"><span data-stu-id="92b5a-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="92b5a-119">O modo adhoc requer que o protocolo use o mecanismo de multicast UDP para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="92b5a-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="92b5a-120">Para obter mais informações sobre a propriedade, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>consulte.</span><span class="sxs-lookup"><span data-stu-id="92b5a-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="92b5a-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="92b5a-121">discoveryVersion</span></span> | <span data-ttu-id="92b5a-122">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="92b5a-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="92b5a-123">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="92b5a-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="92b5a-124">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="92b5a-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="92b5a-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="92b5a-125">maxResponseDelay</span></span> | <span data-ttu-id="92b5a-126">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar determinadas mensagens, como correspondência de investigação ou resolução de correspondência.</span><span class="sxs-lookup"><span data-stu-id="92b5a-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="92b5a-127">Se todos os ProbeMatches forem enviados ao mesmo tempo, um Storm de rede poderá resultar.</span><span class="sxs-lookup"><span data-stu-id="92b5a-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="92b5a-128">Para evitar que isso ocorra, os ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="92b5a-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="92b5a-129">O atraso aleatório está no intervalo de 0 até o valor definido por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="92b5a-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="92b5a-130">Se esse atributo for definido como 0, as mensagens ProbeMatches serão enviadas em um loop rígido sem nenhum atraso.</span><span class="sxs-lookup"><span data-stu-id="92b5a-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="92b5a-131">Caso contrário, as mensagens ProbeMatches são enviadas com um atraso aleatório, de modo que o tempo total necessário para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="92b5a-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="92b5a-132">Esse valor só é relevante para os serviços, não é usado por clientes.</span><span class="sxs-lookup"><span data-stu-id="92b5a-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="92b5a-133">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="92b5a-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="92b5a-134">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="92b5a-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="92b5a-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="92b5a-135">Child elements</span></span>

<span data-ttu-id="92b5a-136">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="92b5a-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92b5a-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="92b5a-137">Parent elements</span></span>

| <span data-ttu-id="92b5a-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="92b5a-138">Element</span></span> | <span data-ttu-id="92b5a-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="92b5a-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="92b5a-140">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="92b5a-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="92b5a-141">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="92b5a-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="92b5a-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92b5a-142">Example</span></span>

<span data-ttu-id="92b5a-143">O exemplo a seguir demonstra um serviço de escuta nas mensagens de descoberta por meio de um transporte de multicast de rede par.</span><span class="sxs-lookup"><span data-stu-id="92b5a-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="92b5a-144">O exemplo especifica explicitamente a versão de abril de 2005 de WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="92b5a-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="92b5a-145">A configuração de ponto de extremidade padrão é definida por serviço e não pode ser compartilhada entre o serviço.</span><span class="sxs-lookup"><span data-stu-id="92b5a-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="92b5a-146">Se outro serviço quiser ter o mesmo ponto de extremidade de descoberta, a mesma configuração precisará ser adicionada à seção desse serviço.</span><span class="sxs-lookup"><span data-stu-id="92b5a-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="92b5a-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92b5a-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
