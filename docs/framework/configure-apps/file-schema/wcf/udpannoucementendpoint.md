---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad3ac58b92c70f32b8a0e6a81f8ebb2b23f25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltudpannoucementendpointgt"></a><span data-ttu-id="0a4f4-102">&lt;udpAnnoucementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="0a4f4-102">&lt;udpAnnoucementEndpoint&gt;</span></span>
<span data-ttu-id="0a4f4-103">Este elemento de configuração define um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de aviso sobre uma associação de UDP.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-103">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="0a4f4-104">Ele tem um contrato fixo e dá suporte a duas versões de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-104">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="0a4f4-105">Além disso, ele tem uma associação de UDP fixa e um valor padrão conforme especificado nas especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery versão 1.1).</span><span class="sxs-lookup"><span data-stu-id="0a4f4-105">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="0a4f4-106">Você pode especificar o endereço de difusão seletiva a ser usado para enviar e receber mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-106">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="0a4f4-107">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0a4f4-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a4f4-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0a4f4-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a4f4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a4f4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a4f4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a4f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a4f4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a4f4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a4f4-112">Attributes</span></span>  
  
|<span data-ttu-id="0a4f4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0a4f4-113">Attribute</span></span>|<span data-ttu-id="0a4f4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a4f4-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="0a4f4-115">discoveryVersion</span></span>|<span data-ttu-id="0a4f4-116">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="0a4f4-117">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="0a4f4-118">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="0a4f4-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="0a4f4-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="0a4f4-120">Um valor Timespan que especifica o valor máximo para o atraso de protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="0a4f4-121">As mensagens de espera para um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="0a4f4-122">Este atributo é usado para definir um atraso aleatório, pequeno para evitar excesso de rede quando sai de uma rede e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="0a4f4-123">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="0a4f4-123">multicastAddress</span></span>|<span data-ttu-id="0a4f4-124">Um URI que especifica um endereço de multicast para usar para enviar e receber mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-124">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="0a4f4-125">O valor padrão é o endereço multicast como compatível com a especificação do protocolo.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-125">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="0a4f4-126">name</span><span class="sxs-lookup"><span data-stu-id="0a4f4-126">name</span></span>|<span data-ttu-id="0a4f4-127">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-127">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0a4f4-128">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-128">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a4f4-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a4f4-129">Child Elements</span></span>  
  
|<span data-ttu-id="0a4f4-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a4f4-130">Element</span></span>|<span data-ttu-id="0a4f4-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4f4-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a4f4-132">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="0a4f4-132">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="0a4f4-133">Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-133">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a4f4-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a4f4-134">Parent Elements</span></span>  
  
|<span data-ttu-id="0a4f4-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a4f4-135">Element</span></span>|<span data-ttu-id="0a4f4-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4f4-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a4f4-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0a4f4-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0a4f4-138">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-138">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a4f4-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a4f4-139">Example</span></span>  
 <span data-ttu-id="0a4f4-140">O exemplo a seguir demonstra um cliente escuta anúncio por um UDP multicast transporte com padrão de endereço de multicast e UDP transporte multicast com o endereço de multicast especificado.</span><span class="sxs-lookup"><span data-stu-id="0a4f4-140">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a4f4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a4f4-141">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
