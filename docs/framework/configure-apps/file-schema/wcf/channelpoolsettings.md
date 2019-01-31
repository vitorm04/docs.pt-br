---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd6cf74560694e7e16103c624b33a4c590ce5d50
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266917"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="04fcc-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="04fcc-101">\<channelPoolSettings></span></span>
<span data-ttu-id="04fcc-102">Especifica as configurações de pool de canal para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="04fcc-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="04fcc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04fcc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="04fcc-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="04fcc-104">\<bindings></span></span>  
<span data-ttu-id="04fcc-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="04fcc-105">\<customBinding></span></span>  
<span data-ttu-id="04fcc-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="04fcc-106">\<binding></span></span>  
<span data-ttu-id="04fcc-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="04fcc-107">\<oneWay></span></span>  
<span data-ttu-id="04fcc-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="04fcc-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04fcc-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04fcc-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04fcc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="04fcc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04fcc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="04fcc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04fcc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="04fcc-112">Attributes</span></span>  
  
|<span data-ttu-id="04fcc-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="04fcc-113">Attribute</span></span>|<span data-ttu-id="04fcc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="04fcc-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="04fcc-115">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo de canais no pool podem ficar ociosos antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="04fcc-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="04fcc-116">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="04fcc-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="04fcc-117">Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool está fechado.</span><span class="sxs-lookup"><span data-stu-id="04fcc-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="04fcc-118">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="04fcc-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="04fcc-119">Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto.</span><span class="sxs-lookup"><span data-stu-id="04fcc-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="04fcc-120">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="04fcc-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04fcc-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="04fcc-121">Child Elements</span></span>  
 <span data-ttu-id="04fcc-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="04fcc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04fcc-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="04fcc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="04fcc-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="04fcc-124">Element</span></span>|<span data-ttu-id="04fcc-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="04fcc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04fcc-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="04fcc-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="04fcc-127">Habilita o roteamento de pacotes para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="04fcc-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04fcc-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="04fcc-128">Remarks</span></span>  
 <span data-ttu-id="04fcc-129">As cotas são usadas como um mecanismo de diretiva para impedir o consumo de recursos em excesso.</span><span class="sxs-lookup"><span data-stu-id="04fcc-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="04fcc-130">Elas impedir ataques de negação de serviço (DOS) que são mal-intencionados ou não intencionais.</span><span class="sxs-lookup"><span data-stu-id="04fcc-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="04fcc-131">Use esse elemento ao definir cotas de canal em um canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="04fcc-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="04fcc-132">`ChannelPoolSettings` Especifica as cotas de três:</span><span class="sxs-lookup"><span data-stu-id="04fcc-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="04fcc-133">O `idleTimeout` cota é usada para reduzir os ataques de negação de serviço (DOS) no servidor que dependem de prender os recursos por um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="04fcc-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="04fcc-134">No cliente, definir o valor correto pode aumentar a confiabilidade de conexão com o serviço.</span><span class="sxs-lookup"><span data-stu-id="04fcc-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="04fcc-135">O valor padrão se baseia em uma forma prudente modesta alocação de recursos.</span><span class="sxs-lookup"><span data-stu-id="04fcc-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="04fcc-136">Ele é adequado para cenários de instalação pequeno e um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="04fcc-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="04fcc-137">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="04fcc-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="04fcc-138">O `leaseTimeout` cota é usada para integração com os balanceadores de carga e aumentar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="04fcc-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="04fcc-139">O valor padrão se baseia em uma alocação conservadora de recursos.</span><span class="sxs-lookup"><span data-stu-id="04fcc-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="04fcc-140">Ele é adequado para cenários de instalação pequeno e um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="04fcc-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="04fcc-141">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="04fcc-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="04fcc-142">O `maxOutboundChannelsPerEndpoint` cota define limites de cache no servidor e o cliente e é usada para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="04fcc-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="04fcc-143">O valor padrão se baseia em uma forma prudente modesta alocação de recursos que é adequada para cenários de instalação pequeno e um ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="04fcc-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="04fcc-144">Os administradores de serviço devem examinar o valor se uma instalação está ficando sem recursos ou se as conexões estão sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="04fcc-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fcc-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04fcc-145">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="04fcc-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="04fcc-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="04fcc-147">Associações</span><span class="sxs-lookup"><span data-stu-id="04fcc-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="04fcc-148">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="04fcc-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="04fcc-149">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="04fcc-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="04fcc-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="04fcc-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
