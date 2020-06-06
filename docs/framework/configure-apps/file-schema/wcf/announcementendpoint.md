---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: decaaa1cea5345ff971b16cbb20a85dd803a52d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850289"
---
# \<announcementEndpoint>
<span data-ttu-id="c8337-101">Este elemento de configuração define um ponto de extremidade padrão com um contrato de anúncio fixo.</span><span class="sxs-lookup"><span data-stu-id="c8337-101">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="c8337-102">Um serviço pode, opcionalmente, anunciar sua disponibilidade enviando uma mensagem de anúncio online e offline quando ela é aberta ou fechada, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c8337-102">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="c8337-103">Um serviço Windows Communication Foundation (WCF) especifica os pontos de extremidade do comunicado no [\<serviceDiscovery>](servicediscovery.md) elemento e usa o AnnouncementClient para executar os anúncios.</span><span class="sxs-lookup"><span data-stu-id="c8337-103">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="c8337-104">Um cliente que deseja escutar o anúncio de outro serviço está realmente agindo como um serviço WCF; Portanto, você precisa configurar os pontos de extremidade do comunicado para esse cliente na [\<services>](services.md) seção.</span><span class="sxs-lookup"><span data-stu-id="c8337-104">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="c8337-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8337-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8337-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c8337-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c8337-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c8337-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8337-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8337-108">Attributes</span></span>  
  
|<span data-ttu-id="c8337-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="c8337-109">Attribute</span></span>|<span data-ttu-id="c8337-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8337-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8337-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="c8337-111">discoveryVersion</span></span>|<span data-ttu-id="c8337-112">Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="c8337-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="c8337-113">Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="c8337-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="c8337-114">Esse valor é do tipo <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="c8337-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="c8337-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="c8337-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="c8337-116">Um valor TimeSpan que especifica o valor máximo para o atraso que o protocolo de descoberta aguardará antes de enviar uma mensagem de saudação.</span><span class="sxs-lookup"><span data-stu-id="c8337-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="c8337-117">As mensagens aguardarão um valor de tempo aleatório entre 0 e o valor desse atributo antes de serem enviadas.</span><span class="sxs-lookup"><span data-stu-id="c8337-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="c8337-118">Esse atributo é usado para definir um atraso pequeno e aleatório para evitar Storm de rede quando uma rede sai e todos os serviços voltam a ficar online ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="c8337-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="c8337-119">name</span><span class="sxs-lookup"><span data-stu-id="c8337-119">name</span></span>|<span data-ttu-id="c8337-120">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="c8337-120">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="c8337-121">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="c8337-121">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8337-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c8337-122">Child Elements</span></span>  
 <span data-ttu-id="c8337-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c8337-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8337-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c8337-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c8337-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8337-125">Element</span></span>|<span data-ttu-id="c8337-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8337-126">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="c8337-127">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="c8337-127">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c8337-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8337-128">Example</span></span>  
 <span data-ttu-id="c8337-129">O exemplo a seguir demonstra um cliente que escuta mensagens de anúncios por http e PEERNET.</span><span class="sxs-lookup"><span data-stu-id="c8337-129">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8337-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8337-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
