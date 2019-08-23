---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926544"
---
# <a name="announcementendpoint"></a><span data-ttu-id="3bd99-101">\<> announcementEndpoint</span><span class="sxs-lookup"><span data-stu-id="3bd99-101">\<announcementEndpoint></span></span>
<span data-ttu-id="3bd99-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato de anúncio fixo.</span><span class="sxs-lookup"><span data-stu-id="3bd99-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="3bd99-103">Um serviço pode, opcionalmente, anunciar sua disponibilidade enviando uma mensagem de anúncio online e offline quando ela é aberta ou fechada, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3bd99-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="3bd99-104">Um serviço Windows Communication Foundation (WCF) especifica os pontos de extremidade do comunicado no elemento de [ \<>](servicediscovery.md) de serviço e usa o AnnouncementClient para executar os anúncios.</span><span class="sxs-lookup"><span data-stu-id="3bd99-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="3bd99-105">Um cliente que deseja escutar o anúncio de outro serviço está realmente agindo como um serviço WCF; Portanto, você precisa configurar os pontos de extremidade do comunicado para esse cliente na [ \<seção Serviços >](services.md) .</span><span class="sxs-lookup"><span data-stu-id="3bd99-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
<span data-ttu-id="3bd99-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3bd99-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="3bd99-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3bd99-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd99-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bd99-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bd99-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3bd99-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3bd99-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3bd99-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bd99-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bd99-111">Attributes</span></span>  
  
|<span data-ttu-id="3bd99-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3bd99-112">Attribute</span></span>|<span data-ttu-id="3bd99-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bd99-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bd99-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="3bd99-114">discoveryVersion</span></span>|<span data-ttu-id="3bd99-115">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="3bd99-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="3bd99-116">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="3bd99-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="3bd99-117">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="3bd99-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="3bd99-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="3bd99-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="3bd99-119">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="3bd99-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="3bd99-120">As mensagens aguardarão um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviadas.</span><span class="sxs-lookup"><span data-stu-id="3bd99-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="3bd99-121">Esse atributo é usado para definir um atraso pequeno e aleatório para evitar Storm de rede quando uma rede sai e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="3bd99-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="3bd99-122">name</span><span class="sxs-lookup"><span data-stu-id="3bd99-122">name</span></span>|<span data-ttu-id="3bd99-123">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3bd99-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="3bd99-124">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="3bd99-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bd99-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3bd99-125">Child Elements</span></span>  
 <span data-ttu-id="3bd99-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3bd99-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bd99-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3bd99-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3bd99-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bd99-128">Element</span></span>|<span data-ttu-id="3bd99-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bd99-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bd99-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3bd99-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="3bd99-131">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="3bd99-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3bd99-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bd99-132">Example</span></span>  
 <span data-ttu-id="3bd99-133">O exemplo a seguir demonstra um cliente que escuta mensagens de anúncios por http e PEERNET.</span><span class="sxs-lookup"><span data-stu-id="3bd99-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bd99-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bd99-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
