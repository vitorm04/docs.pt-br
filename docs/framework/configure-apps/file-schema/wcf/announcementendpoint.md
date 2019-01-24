---
title: '&lt;announcementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 8e180d53260ccf3364ab3c8d7b076f78917526d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729873"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="1da71-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="1da71-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="1da71-103">Este elemento de configuração define um ponto de extremidade padrão com um contrato de anúncio fixo.</span><span class="sxs-lookup"><span data-stu-id="1da71-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="1da71-104">Um serviço pode, opcionalmente, anunciar sua disponibilidade, enviando uma mensagem de comunicado online e offline, quando ele é aberto ou fechado, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1da71-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="1da71-105">Um serviço do Windows Communication Foundation (WCF) especifica os pontos de extremidade de comunicado na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento e usa o AnnouncementClient para executar os anúncios.</span><span class="sxs-lookup"><span data-stu-id="1da71-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="1da71-106">Um cliente que desejarem escutar o comunicado de outro serviço, na verdade, está atuando como um serviço WCF. Portanto, você precisa configurar os pontos de extremidade de comunicado para esse cliente na [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção.</span><span class="sxs-lookup"><span data-stu-id="1da71-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="1da71-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1da71-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="1da71-108">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1da71-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da71-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1da71-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1da71-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1da71-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1da71-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1da71-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1da71-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1da71-112">Attributes</span></span>  
  
|<span data-ttu-id="1da71-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1da71-113">Attribute</span></span>|<span data-ttu-id="1da71-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1da71-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1da71-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1da71-115">discoveryVersion</span></span>|<span data-ttu-id="1da71-116">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1da71-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1da71-117">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="1da71-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1da71-118">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="1da71-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1da71-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="1da71-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="1da71-120">Um valor de Timespan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="1da71-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="1da71-121">As mensagens esperará um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="1da71-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="1da71-122">Este atributo é usado para definir um atraso de pequeno e aleatório para impedir o excesso de rede quando sai de uma rede e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="1da71-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="1da71-123">name</span><span class="sxs-lookup"><span data-stu-id="1da71-123">name</span></span>|<span data-ttu-id="1da71-124">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="1da71-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1da71-125">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="1da71-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1da71-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1da71-126">Child Elements</span></span>  
 <span data-ttu-id="1da71-127">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1da71-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1da71-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1da71-128">Parent Elements</span></span>  
  
|<span data-ttu-id="1da71-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="1da71-129">Element</span></span>|<span data-ttu-id="1da71-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="1da71-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1da71-131">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1da71-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1da71-132">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="1da71-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1da71-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1da71-133">Example</span></span>  
 <span data-ttu-id="1da71-134">O exemplo a seguir demonstra um cliente escuta para mensagens de anúncios via http e peernet.</span><span class="sxs-lookup"><span data-stu-id="1da71-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="1da71-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da71-135">See also</span></span>
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
