---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398166"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="695a0-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="695a0-101">\<channelPoolSettings></span></span>
<span data-ttu-id="695a0-102">Especifica as configurações de pool de canais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="695a0-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
<span data-ttu-id="695a0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="695a0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="695a0-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="695a0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="695a0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="695a0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="695a0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="695a0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="695a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="695a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="695a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oneWay >** ](oneway.md)</span><span class="sxs-lookup"><span data-stu-id="695a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)</span></span>\
<span data-ttu-id="695a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> channelPoolSettings**</span><span class="sxs-lookup"><span data-stu-id="695a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="695a0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="695a0-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="695a0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="695a0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="695a0-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="695a0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="695a0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="695a0-113">Attributes</span></span>  
  
|<span data-ttu-id="695a0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="695a0-114">Attribute</span></span>|<span data-ttu-id="695a0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="695a0-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="695a0-116">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que os canais no pool podem ficar ociosos antes de serem desconectados.</span><span class="sxs-lookup"><span data-stu-id="695a0-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="695a0-117">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="695a0-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="695a0-118">Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool, é fechado.</span><span class="sxs-lookup"><span data-stu-id="695a0-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="695a0-119">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="695a0-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="695a0-120">Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto.</span><span class="sxs-lookup"><span data-stu-id="695a0-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="695a0-121">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="695a0-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="695a0-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="695a0-122">Child Elements</span></span>  
 <span data-ttu-id="695a0-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="695a0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="695a0-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="695a0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="695a0-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="695a0-125">Element</span></span>|<span data-ttu-id="695a0-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="695a0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="695a0-127">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="695a0-127">\<oneWay></span></span>](oneway.md)|<span data-ttu-id="695a0-128">Habilita o roteamento de pacotes para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="695a0-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="695a0-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="695a0-129">Remarks</span></span>  
 <span data-ttu-id="695a0-130">As cotas são usadas como um mecanismo de política para evitar o consumo de recursos excessivos.</span><span class="sxs-lookup"><span data-stu-id="695a0-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="695a0-131">Eles impedem ataques de DOS (negação de serviço) que são mal-intencionados ou não intencionais.</span><span class="sxs-lookup"><span data-stu-id="695a0-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="695a0-132">Use este elemento ao definir cotas de canal em um canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="695a0-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="695a0-133">`ChannelPoolSettings`especifica três cotas:</span><span class="sxs-lookup"><span data-stu-id="695a0-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="695a0-134">A `idleTimeout` cota é usada para atenuar ataques de dos (negação de serviço) no servidor que dependem da vinculação de recursos por um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="695a0-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="695a0-135">No cliente, a definição do valor correto pode aumentar a confiabilidade da conexão com o serviço.</span><span class="sxs-lookup"><span data-stu-id="695a0-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="695a0-136">O valor padrão é baseado em uma alocação conservadormente modesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="695a0-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="695a0-137">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="695a0-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="695a0-138">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="695a0-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="695a0-139">A `leaseTimeout` cota é usada para a integração com balanceadores de carga e para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="695a0-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="695a0-140">O valor padrão é baseado em uma alocação conservadora de recursos.</span><span class="sxs-lookup"><span data-stu-id="695a0-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="695a0-141">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="695a0-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="695a0-142">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="695a0-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="695a0-143">A `maxOutboundChannelsPerEndpoint` cota define os limites de cache no servidor e no cliente e é usada para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="695a0-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="695a0-144">O valor padrão é baseado em uma alocação conservadormente modesto de recursos que é adequada para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="695a0-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="695a0-145">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="695a0-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695a0-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="695a0-146">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="695a0-147">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="695a0-147">\<oneWay></span></span>](oneway.md)
- [<span data-ttu-id="695a0-148">Associações</span><span class="sxs-lookup"><span data-stu-id="695a0-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="695a0-149">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="695a0-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="695a0-150">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="695a0-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="695a0-151">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="695a0-151">\<customBinding></span></span>](custombinding.md)
