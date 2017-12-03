---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d48f3b304b337ba61f53bbd81cac8601bc68cb0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="20e5a-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="20e5a-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="20e5a-103">Especifica as configurações de pool do canal para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="20e5a-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="20e5a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="20e5a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="20e5a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="20e5a-105">\<bindings></span></span>  
<span data-ttu-id="20e5a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="20e5a-106">\<customBinding></span></span>  
<span data-ttu-id="20e5a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="20e5a-107">\<binding></span></span>  
<span data-ttu-id="20e5a-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="20e5a-108">\<oneWay></span></span>  
<span data-ttu-id="20e5a-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="20e5a-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e5a-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20e5a-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20e5a-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20e5a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="20e5a-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20e5a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20e5a-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="20e5a-113">Attributes</span></span>  
  
|<span data-ttu-id="20e5a-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="20e5a-114">Attribute</span></span>|<span data-ttu-id="20e5a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e5a-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="20e5a-116">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo de canais no pool podem ficar ociosos antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="20e5a-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="20e5a-117">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="20e5a-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="20e5a-118">Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool está fechado.</span><span class="sxs-lookup"><span data-stu-id="20e5a-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="20e5a-119">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="20e5a-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="20e5a-120">Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto.</span><span class="sxs-lookup"><span data-stu-id="20e5a-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="20e5a-121">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="20e5a-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20e5a-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20e5a-122">Child Elements</span></span>  
 <span data-ttu-id="20e5a-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="20e5a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20e5a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20e5a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="20e5a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="20e5a-125">Element</span></span>|<span data-ttu-id="20e5a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e5a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20e5a-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="20e5a-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="20e5a-128">Permite que o roteamento de pacotes para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="20e5a-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20e5a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="20e5a-129">Remarks</span></span>  
 <span data-ttu-id="20e5a-130">As cotas são usadas como um mecanismo de política para evitar o consumo de recursos em excesso.</span><span class="sxs-lookup"><span data-stu-id="20e5a-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="20e5a-131">Elas impedem ataques de negação de serviço (DOS) que são mal-intencionados ou não intencionais.</span><span class="sxs-lookup"><span data-stu-id="20e5a-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="20e5a-132">Use esse elemento ao definir cotas de canal em um canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="20e5a-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="20e5a-133">`ChannelPoolSettings`Especifica as cotas de três:</span><span class="sxs-lookup"><span data-stu-id="20e5a-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="20e5a-134">O `idleTimeout` cota é usada para reduzir os ataques de negação de serviço (DOS) no servidor que se baseiam na prender os recursos por um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="20e5a-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="20e5a-135">No cliente, definir o valor correto pode aumentar a confiabilidade de conexão com o serviço.</span><span class="sxs-lookup"><span data-stu-id="20e5a-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="20e5a-136">O valor padrão baseia-se em uma forma prudente modesta alocação de recursos.</span><span class="sxs-lookup"><span data-stu-id="20e5a-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="20e5a-137">Ele é adequado para um ambiente de desenvolvimento e cenários de instalação pequeno.</span><span class="sxs-lookup"><span data-stu-id="20e5a-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="20e5a-138">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="20e5a-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="20e5a-139">O `leaseTimeout` cota é usada para integração com balanceadores de carga e para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="20e5a-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="20e5a-140">O valor padrão baseia-se em uma alocação de recursos de conservadora.</span><span class="sxs-lookup"><span data-stu-id="20e5a-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="20e5a-141">Ele é adequado para um ambiente de desenvolvimento e cenários de instalação pequeno.</span><span class="sxs-lookup"><span data-stu-id="20e5a-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="20e5a-142">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="20e5a-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="20e5a-143">O `maxOutboundChannelsPerEndpoint` cota define limites de cache no servidor e o cliente e é usada para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="20e5a-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="20e5a-144">O valor padrão baseia-se em uma forma prudente modesta alocação de recursos que é adequada para um ambiente de desenvolvimento e cenários de instalação pequeno.</span><span class="sxs-lookup"><span data-stu-id="20e5a-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="20e5a-145">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas apesar da disponibilidade dos recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="20e5a-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e5a-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e5a-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="20e5a-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="20e5a-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 <span data-ttu-id="20e5a-148">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="20e5a-148">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="20e5a-149">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="20e5a-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="20e5a-150">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="20e5a-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="20e5a-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="20e5a-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
