---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 8977a36d9eee48505a65fa52272a95665fea7972
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267086"
---
# <a name="announcementendpoint"></a><span data-ttu-id="47f65-101">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="47f65-101">\<announcementEndpoint></span></span>
<span data-ttu-id="47f65-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato de anúncio fixo.</span><span class="sxs-lookup"><span data-stu-id="47f65-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="47f65-103">Um serviço pode, opcionalmente, anunciar sua disponibilidade, enviando uma mensagem de comunicado online e offline, quando ele é aberto ou fechado, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="47f65-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="47f65-104">Um serviço do Windows Communication Foundation (WCF) especifica os pontos de extremidade de comunicado na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento e usa o AnnouncementClient para executar os anúncios.</span><span class="sxs-lookup"><span data-stu-id="47f65-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="47f65-105">Um cliente que desejarem escutar o comunicado de outro serviço, na verdade, está atuando como um serviço WCF. Portanto, você precisa configurar os pontos de extremidade de comunicado para esse cliente na [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção.</span><span class="sxs-lookup"><span data-stu-id="47f65-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="47f65-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="47f65-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="47f65-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="47f65-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f65-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47f65-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47f65-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47f65-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47f65-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47f65-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47f65-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="47f65-111">Attributes</span></span>  
  
|<span data-ttu-id="47f65-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="47f65-112">Attribute</span></span>|<span data-ttu-id="47f65-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="47f65-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47f65-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="47f65-114">discoveryVersion</span></span>|<span data-ttu-id="47f65-115">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="47f65-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="47f65-116">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="47f65-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="47f65-117">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="47f65-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="47f65-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="47f65-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="47f65-119">Um valor de Timespan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="47f65-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="47f65-120">As mensagens esperará um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviados.</span><span class="sxs-lookup"><span data-stu-id="47f65-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="47f65-121">Este atributo é usado para definir um atraso de pequeno e aleatório para impedir o excesso de rede quando sai de uma rede e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="47f65-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="47f65-122">name</span><span class="sxs-lookup"><span data-stu-id="47f65-122">name</span></span>|<span data-ttu-id="47f65-123">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="47f65-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="47f65-124">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="47f65-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47f65-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47f65-125">Child Elements</span></span>  
 <span data-ttu-id="47f65-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="47f65-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47f65-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47f65-127">Parent Elements</span></span>  
  
|<span data-ttu-id="47f65-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="47f65-128">Element</span></span>|<span data-ttu-id="47f65-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="47f65-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47f65-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="47f65-130">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="47f65-131">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="47f65-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="47f65-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47f65-132">Example</span></span>  
 <span data-ttu-id="47f65-133">O exemplo a seguir demonstra um cliente escuta para mensagens de anúncios via http e peernet.</span><span class="sxs-lookup"><span data-stu-id="47f65-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47f65-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47f65-134">See also</span></span>
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
