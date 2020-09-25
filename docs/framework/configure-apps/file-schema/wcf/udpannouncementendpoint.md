---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 67503b1bc3c6282ff5018adc20acbb89de49ba50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173751"
---
# \<udpAnnouncementEndpoint>

<span data-ttu-id="b6922-101">Este elemento de configuração define um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de anúncio por uma associação UDP.</span><span class="sxs-lookup"><span data-stu-id="b6922-101">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="b6922-102">Ele tem um contrato fixo e dá suporte a duas versões de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b6922-102">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="b6922-103">Além disso, ele tem uma associação de UDP fixa e um valor de endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery versão 1.1).</span><span class="sxs-lookup"><span data-stu-id="b6922-103">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="b6922-104">Você pode especificar o endereço de multicast a ser usado para enviar e receber as mensagens de anúncio.</span><span class="sxs-lookup"><span data-stu-id="b6922-104">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="b6922-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6922-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6922-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6922-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b6922-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6922-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6922-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6922-108">Attributes</span></span>  
  
|<span data-ttu-id="b6922-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="b6922-109">Attribute</span></span>|<span data-ttu-id="b6922-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6922-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6922-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="b6922-111">discoveryVersion</span></span>|<span data-ttu-id="b6922-112">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="b6922-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="b6922-113">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="b6922-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="b6922-114">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="b6922-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="b6922-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="b6922-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="b6922-116">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="b6922-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="b6922-117">As mensagens aguardarão um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviadas.</span><span class="sxs-lookup"><span data-stu-id="b6922-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="b6922-118">Esse atributo é usado para definir um atraso pequeno e aleatório para evitar Storm de rede quando uma rede sai e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b6922-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="b6922-119">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="b6922-119">multicastAddress</span></span>|<span data-ttu-id="b6922-120">Um URI que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="b6922-120">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="b6922-121">O valor padrão é o endereço de multicast como compatível com a especificação de protocolo.</span><span class="sxs-lookup"><span data-stu-id="b6922-121">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="b6922-122">name</span><span class="sxs-lookup"><span data-stu-id="b6922-122">name</span></span>|<span data-ttu-id="b6922-123">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="b6922-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="b6922-124">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="b6922-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6922-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6922-125">Child Elements</span></span>  
  
|<span data-ttu-id="b6922-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6922-126">Element</span></span>|<span data-ttu-id="b6922-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6922-127">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="b6922-128">Uma coleção de configurações que permitem configurar o transporte UDP para o ponto de extremidade UDP.</span><span class="sxs-lookup"><span data-stu-id="b6922-128">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6922-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6922-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b6922-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6922-130">Element</span></span>|<span data-ttu-id="b6922-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6922-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b6922-132">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="b6922-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6922-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6922-133">Example</span></span>  

 <span data-ttu-id="b6922-134">O exemplo a seguir demonstra um cliente ouvindo o anúncio em um transporte multicast UDP com o endereço multicast padrão e o transporte multicast UDP com o endereço multicast especificado.</span><span class="sxs-lookup"><span data-stu-id="b6922-134">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6922-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6922-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
