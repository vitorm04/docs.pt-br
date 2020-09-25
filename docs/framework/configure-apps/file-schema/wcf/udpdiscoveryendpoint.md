---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: f02cbddcdd4390d754f93e6f6d9aae6646cb137b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183618"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="da567-101">Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta em uma associação de multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="da567-101">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="da567-102">Esse ponto de extremidade tem um contrato fixo e dá suporte a duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="da567-102">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="da567-103">Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).</span><span class="sxs-lookup"><span data-stu-id="da567-103">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="da567-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da567-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da567-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da567-105">Attributes and Elements</span></span>  

 <span data-ttu-id="da567-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="da567-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da567-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="da567-107">Attributes</span></span>  
  
|<span data-ttu-id="da567-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="da567-108">Attribute</span></span>|<span data-ttu-id="da567-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="da567-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da567-110">DiscoveryMode</span><span class="sxs-lookup"><span data-stu-id="da567-110">discoveryMode</span></span>|<span data-ttu-id="da567-111">Uma cadeia de caracteres que especifica o modo do protocolo de descoberta.</span><span class="sxs-lookup"><span data-stu-id="da567-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="da567-112">Os valores válidos são "adhoc" e "Managed".</span><span class="sxs-lookup"><span data-stu-id="da567-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="da567-113">No modo gerenciado, o protocolo depende de um proxy de descoberta, que atua como um repositório de serviços detectáveis.</span><span class="sxs-lookup"><span data-stu-id="da567-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="da567-114">O modo adhoc requer que o protocolo use o mecanismo de multicast UDP para localizar os serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="da567-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="da567-115">Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="da567-115">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="da567-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="da567-116">discoveryVersion</span></span>|<span data-ttu-id="da567-117">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="da567-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="da567-118">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="da567-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="da567-119">Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="da567-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="da567-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="da567-120">maxResponseDelay</span></span>|<span data-ttu-id="da567-121">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar determinadas mensagens, como correspondência de investigação ou resolução de correspondência.</span><span class="sxs-lookup"><span data-stu-id="da567-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="da567-122">Se todos os ProbeMatches forem enviados ao mesmo tempo, um Storm de rede poderá resultar.</span><span class="sxs-lookup"><span data-stu-id="da567-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="da567-123">Para evitar que isso ocorra, os ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch.</span><span class="sxs-lookup"><span data-stu-id="da567-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="da567-124">O atraso aleatório está no intervalo de 0 até o valor definido por esse atributo.</span><span class="sxs-lookup"><span data-stu-id="da567-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="da567-125">Se esse atributo for definido como 0, as mensagens ProbeMatches serão enviadas em um loop rígido sem nenhum atraso.</span><span class="sxs-lookup"><span data-stu-id="da567-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="da567-126">Caso contrário, as mensagens ProbeMatches são enviadas com um atraso aleatório, de modo que o tempo total necessário para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="da567-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="da567-127">Esse valor só é relevante para os serviços, não é usado por clientes.</span><span class="sxs-lookup"><span data-stu-id="da567-127">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="da567-128">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="da567-128">multicastAddress</span></span>|<span data-ttu-id="da567-129">Um URI que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="da567-129">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="da567-130">O valor padrão é o endereço de multicast como compatível com a especificação de protocolo.</span><span class="sxs-lookup"><span data-stu-id="da567-130">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="da567-131">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="da567-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="da567-132">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="da567-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da567-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da567-133">Child Elements</span></span>  
  
|<span data-ttu-id="da567-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="da567-134">Element</span></span>|<span data-ttu-id="da567-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="da567-135">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="da567-136">Uma coleção de configurações que permitem configurar o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="da567-136">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da567-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="da567-137">Parent Elements</span></span>  
  
|<span data-ttu-id="da567-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="da567-138">Element</span></span>|<span data-ttu-id="da567-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="da567-139">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="da567-140">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="da567-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da567-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da567-141">Example</span></span>  

 <span data-ttu-id="da567-142">O exemplo a seguir demonstra um serviço de escuta de mensagens de descoberta em um transporte multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="da567-142">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da567-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="da567-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
