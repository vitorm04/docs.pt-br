---
title: '&lt;DiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747392"
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="95e03-102">&lt;DiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="95e03-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="95e03-103">Este elemento de configuração define um ponto de extremidade padrão com um contrato de correção da descoberta.</span><span class="sxs-lookup"><span data-stu-id="95e03-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="95e03-104">Quando adicionado à configuração de serviço, ele especifica onde ouvir as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="95e03-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="95e03-105">Quando adicionado à configuração de cliente especifica para onde enviar as consultas de descoberta.</span><span class="sxs-lookup"><span data-stu-id="95e03-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="95e03-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="95e03-106">\<system.serviceModel></span></span>  
<span data-ttu-id="95e03-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="95e03-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e03-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95e03-108">Syntax</span></span>

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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95e03-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="95e03-109">Attributes and elements</span></span>

<span data-ttu-id="95e03-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="95e03-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95e03-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="95e03-111">Attributes</span></span>

| <span data-ttu-id="95e03-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="95e03-112">Attribute</span></span>        | <span data-ttu-id="95e03-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="95e03-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="95e03-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="95e03-114">discoveryMode</span></span>    | <span data-ttu-id="95e03-115">Uma cadeia de caracteres que especifica o modo de protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="95e03-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="95e03-116">Os valores válidos são "Ad hoc" e "Gerenciado".</span><span class="sxs-lookup"><span data-stu-id="95e03-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="95e03-117">No modo gerenciado o protocolo depende de um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos.</span><span class="sxs-lookup"><span data-stu-id="95e03-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="95e03-118">Modo ad hoc requer o protocolo a usar UDP multicast mecanismo para localizar serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="95e03-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="95e03-119">Para obter mais informações sobre a propriedade, consulte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="95e03-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="95e03-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="95e03-120">discoveryVersion</span></span> | <span data-ttu-id="95e03-121">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="95e03-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="95e03-122">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="95e03-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="95e03-123">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="95e03-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="95e03-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="95e03-124">maxResponseDelay</span></span> | <span data-ttu-id="95e03-125">Um valor Timespan que especifica o valor máximo para o protocolo de descoberta de atraso aguardará antes de enviar determinadas mensagens, como teste de correspondência ou resolva.</span><span class="sxs-lookup"><span data-stu-id="95e03-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="95e03-126">Se todas as ProbeMatches forem enviados ao mesmo tempo, pode resultar uma profusão de rede.</span><span class="sxs-lookup"><span data-stu-id="95e03-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="95e03-127">Para evitar que isso ocorra, ProbeMatches são enviadas com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="95e03-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="95e03-128">É o atraso aleatório no intervalo de 0 até o valor definido por este atributo.</span><span class="sxs-lookup"><span data-stu-id="95e03-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="95e03-129">Se esse atributo é definido como 0, as mensagens de ProbeMatches são enviadas em um loop estreito sem atraso.</span><span class="sxs-lookup"><span data-stu-id="95e03-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="95e03-130">Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total gasto para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="95e03-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="95e03-131">Esse valor só é relevante para serviços, ele não é usado por clientes.</span><span class="sxs-lookup"><span data-stu-id="95e03-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="95e03-132">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="95e03-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="95e03-133">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="95e03-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="95e03-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="95e03-134">Child elements</span></span>

<span data-ttu-id="95e03-135">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="95e03-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95e03-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="95e03-136">Parent elements</span></span>

| <span data-ttu-id="95e03-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="95e03-137">Element</span></span> | <span data-ttu-id="95e03-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="95e03-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="95e03-139">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="95e03-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="95e03-140">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="95e03-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="95e03-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95e03-141">Example</span></span>

<span data-ttu-id="95e03-142">O exemplo a seguir demonstra um serviço que escuta as mensagens de descoberta por um transporte de multicast de rede ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="95e03-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="95e03-143">O exemplo especifica explicitamente o WS-Discovery versão de abril de 2005.</span><span class="sxs-lookup"><span data-stu-id="95e03-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="95e03-144">A configuração de ponto de extremidade padrão é definida por serviço e não pode ser compartilhada entre o serviço.</span><span class="sxs-lookup"><span data-stu-id="95e03-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="95e03-145">Se desejar outro serviço que têm o mesmo ponto de extremidade de descoberta, a mesma configuração precisa ser adicionada à seção do serviço.</span><span class="sxs-lookup"><span data-stu-id="95e03-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95e03-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95e03-146">See also</span></span>

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
