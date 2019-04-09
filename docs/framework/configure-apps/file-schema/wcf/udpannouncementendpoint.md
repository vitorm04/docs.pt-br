---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 04f5fb27a0da7e553ff3c0308f7fb2e2df2e0b20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210003"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="a4345-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="a4345-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="a4345-102">Este elemento de configuração define um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de comunicado por uma associação de UDP.</span><span class="sxs-lookup"><span data-stu-id="a4345-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="a4345-103">Ele tem um contrato fixo e oferece suporte a duas versões de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a4345-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="a4345-104">Além disso, ele tem uma associação de UDP fixa e um valor de endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery versão 1.1).</span><span class="sxs-lookup"><span data-stu-id="a4345-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="a4345-105">Você pode especificar o endereço multicast a ser usado para enviar e receber mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="a4345-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="a4345-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4345-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4345-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a4345-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4345-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4345-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4345-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4345-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a4345-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a4345-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4345-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4345-111">Attributes</span></span>  
  
|<span data-ttu-id="a4345-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="a4345-112">Attribute</span></span>|<span data-ttu-id="a4345-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4345-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4345-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="a4345-114">discoveryVersion</span></span>|<span data-ttu-id="a4345-115">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="a4345-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="a4345-116">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="a4345-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="a4345-117">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="a4345-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="a4345-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="a4345-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="a4345-119">Um valor de Timespan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="a4345-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="a4345-120">As mensagens esperará um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="a4345-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="a4345-121">Este atributo é usado para definir um atraso de pequeno e aleatório para impedir o excesso de rede quando sai de uma rede e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a4345-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="a4345-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="a4345-122">multicastAddress</span></span>|<span data-ttu-id="a4345-123">Um URI que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="a4345-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="a4345-124">O valor padrão é o endereço multicast como em conformidade com a especificação do protocolo.</span><span class="sxs-lookup"><span data-stu-id="a4345-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="a4345-125">name</span><span class="sxs-lookup"><span data-stu-id="a4345-125">name</span></span>|<span data-ttu-id="a4345-126">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="a4345-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a4345-127">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="a4345-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4345-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4345-128">Child Elements</span></span>  
  
|<span data-ttu-id="a4345-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4345-129">Element</span></span>|<span data-ttu-id="a4345-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4345-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4345-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="a4345-131">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="a4345-132">Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="a4345-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4345-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4345-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a4345-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4345-134">Element</span></span>|<span data-ttu-id="a4345-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4345-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4345-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="a4345-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="a4345-137">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="a4345-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4345-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4345-138">Example</span></span>  
 <span data-ttu-id="a4345-139">O exemplo a seguir demonstra um cliente escuta de comunicado por um UDP padrão de transporte de multicast com o endereço de multicast e UDP multicast transporte com o endereço multicast especificado.</span><span class="sxs-lookup"><span data-stu-id="a4345-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="a4345-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4345-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
