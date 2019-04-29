---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704044"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="9c0ea-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="9c0ea-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="9c0ea-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato de correção da descoberta.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="9c0ea-103">Quando adicionado à configuração de serviço, ele especifica onde a escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="9c0ea-104">Quando adicionado à configuração de cliente, ele especifica para onde enviar as consultas de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="9c0ea-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9c0ea-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9c0ea-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9c0ea-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0ea-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c0ea-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c0ea-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c0ea-108">Attributes and elements</span></span>

<span data-ttu-id="9c0ea-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c0ea-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c0ea-110">Attributes</span></span>

| <span data-ttu-id="9c0ea-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c0ea-111">Attribute</span></span>        | <span data-ttu-id="9c0ea-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c0ea-112">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="9c0ea-113">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="9c0ea-113">discoveryMode</span></span>    | <span data-ttu-id="9c0ea-114">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-114">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="9c0ea-115">Os valores válidos são "Adhoc" e "Gerenciado".</span><span class="sxs-lookup"><span data-stu-id="9c0ea-115">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="9c0ea-116">No modo gerenciado o protocolo se baseia em um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-116">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="9c0ea-117">Modo ad hoc requer o protocolo a usar o UDP multicast mecanismo para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-117">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="9c0ea-118">Para obter mais informações sobre a propriedade, consulte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-118">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="9c0ea-119">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="9c0ea-119">discoveryVersion</span></span> | <span data-ttu-id="9c0ea-120">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-120">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="9c0ea-121">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-121">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="9c0ea-122">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-122">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="9c0ea-123">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="9c0ea-123">maxResponseDelay</span></span> | <span data-ttu-id="9c0ea-124">Um valor de Timespan que especifica o valor máximo para o atraso, o protocolo de descoberta irá esperar antes de enviar determinadas mensagens, como correspondência de investigação ou resolver.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-124">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="9c0ea-125">Se todas as ProbeMatches forem enviadas ao mesmo tempo, pode resultar uma tempestade de rede.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-125">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="9c0ea-126">Para evitar que isso ocorra, ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-126">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="9c0ea-127">É o atraso aleatório no intervalo de 0 até o valor definido por este atributo.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-127">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="9c0ea-128">Se esse atributo é definido como 0, as ProbeMatches de mensagens são enviadas em um loop estreito sem demora.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-128">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="9c0ea-129">Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total decorrido para enviar mensagens de todas as ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-129">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="9c0ea-130">Esse valor só é relevante para os serviços, ele não é usado pelos clientes.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-130">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="9c0ea-131">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="9c0ea-132">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="9c0ea-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c0ea-133">Child elements</span></span>

<span data-ttu-id="9c0ea-134">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c0ea-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c0ea-135">Parent elements</span></span>

| <span data-ttu-id="9c0ea-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c0ea-136">Element</span></span> | <span data-ttu-id="9c0ea-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c0ea-137">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="9c0ea-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9c0ea-138">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="9c0ea-139">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="9c0ea-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c0ea-140">Example</span></span>

<span data-ttu-id="9c0ea-141">O exemplo a seguir demonstra um serviço escutando em mensagens de descoberta em um transporte de multicast rede ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-141">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="9c0ea-142">O exemplo especifica explicitamente o WS-Discovery versão de abril de 2005.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-142">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="9c0ea-143">A configuração de ponto de extremidade padrão é definida por serviço e não pode ser compartilhada entre o serviço.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-143">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="9c0ea-144">Se outro serviço gostaria de ter o mesmo ponto de extremidade de descoberta, a mesma configuração precisa ser adicionado à seção do serviço.</span><span class="sxs-lookup"><span data-stu-id="9c0ea-144">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c0ea-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c0ea-145">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
