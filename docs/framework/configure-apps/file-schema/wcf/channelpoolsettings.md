---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919551"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="2ad15-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="2ad15-101">\<channelPoolSettings></span></span>
<span data-ttu-id="2ad15-102">Especifica as configurações de pool de canais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2ad15-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="2ad15-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2ad15-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2ad15-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2ad15-104">\<bindings></span></span>  
<span data-ttu-id="2ad15-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2ad15-105">\<customBinding></span></span>  
<span data-ttu-id="2ad15-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="2ad15-106">\<binding></span></span>  
<span data-ttu-id="2ad15-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2ad15-107">\<oneWay></span></span>  
<span data-ttu-id="2ad15-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="2ad15-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad15-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ad15-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ad15-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2ad15-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ad15-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2ad15-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ad15-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2ad15-112">Attributes</span></span>  
  
|<span data-ttu-id="2ad15-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2ad15-113">Attribute</span></span>|<span data-ttu-id="2ad15-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ad15-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="2ad15-115">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que os canais no pool podem ficar ociosos antes de serem desconectados.</span><span class="sxs-lookup"><span data-stu-id="2ad15-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="2ad15-116">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="2ad15-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="2ad15-117">Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool, é fechado.</span><span class="sxs-lookup"><span data-stu-id="2ad15-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="2ad15-118">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2ad15-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="2ad15-119">Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto.</span><span class="sxs-lookup"><span data-stu-id="2ad15-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="2ad15-120">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="2ad15-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ad15-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2ad15-121">Child Elements</span></span>  
 <span data-ttu-id="2ad15-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2ad15-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ad15-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2ad15-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2ad15-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ad15-124">Element</span></span>|<span data-ttu-id="2ad15-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ad15-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ad15-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2ad15-126">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="2ad15-127">Habilita o roteamento de pacotes para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2ad15-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ad15-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ad15-128">Remarks</span></span>  
 <span data-ttu-id="2ad15-129">As cotas são usadas como um mecanismo de política para evitar o consumo de recursos excessivos.</span><span class="sxs-lookup"><span data-stu-id="2ad15-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="2ad15-130">Eles impedem ataques de DOS (negação de serviço) que são mal-intencionados ou não intencionais.</span><span class="sxs-lookup"><span data-stu-id="2ad15-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="2ad15-131">Use este elemento ao definir cotas de canal em um canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="2ad15-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="2ad15-132">`ChannelPoolSettings`especifica três cotas:</span><span class="sxs-lookup"><span data-stu-id="2ad15-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="2ad15-133">A `idleTimeout` cota é usada para atenuar ataques de dos (negação de serviço) no servidor que dependem da vinculação de recursos por um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="2ad15-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="2ad15-134">No cliente, a definição do valor correto pode aumentar a confiabilidade da conexão com o serviço.</span><span class="sxs-lookup"><span data-stu-id="2ad15-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="2ad15-135">O valor padrão é baseado em uma alocação conservadormente modesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="2ad15-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="2ad15-136">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="2ad15-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2ad15-137">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ad15-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="2ad15-138">A `leaseTimeout` cota é usada para a integração com balanceadores de carga e para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="2ad15-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="2ad15-139">O valor padrão é baseado em uma alocação conservadora de recursos.</span><span class="sxs-lookup"><span data-stu-id="2ad15-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="2ad15-140">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="2ad15-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2ad15-141">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ad15-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="2ad15-142">A `maxOutboundChannelsPerEndpoint` cota define os limites de cache no servidor e no cliente e é usada para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="2ad15-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="2ad15-143">O valor padrão é baseado em uma alocação conservadormente modesto de recursos que é adequada para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="2ad15-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="2ad15-144">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ad15-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad15-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ad15-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2ad15-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="2ad15-146">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="2ad15-147">Associações</span><span class="sxs-lookup"><span data-stu-id="2ad15-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2ad15-148">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="2ad15-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2ad15-149">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="2ad15-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2ad15-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2ad15-150">\<customBinding></span></span>](custombinding.md)
