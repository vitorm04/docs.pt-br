---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398166"
---
# \<channelPoolSettings>
<span data-ttu-id="a181e-101">Especifica as configurações de pool de canais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a181e-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a181e-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a181e-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a181e-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a181e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a181e-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a181e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a181e-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="a181e-105">Attributes</span></span>  
  
|<span data-ttu-id="a181e-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="a181e-106">Attribute</span></span>|<span data-ttu-id="a181e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a181e-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="a181e-108">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que os canais no pool podem ficar ociosos antes de serem desconectados.</span><span class="sxs-lookup"><span data-stu-id="a181e-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="a181e-109">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="a181e-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="a181e-110">Um <xref:System.TimeSpan> que especifica o intervalo de tempo após o qual um canal, quando retornado para o pool, é fechado.</span><span class="sxs-lookup"><span data-stu-id="a181e-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="a181e-111">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a181e-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="a181e-112">Um inteiro positivo que especifica o número máximo de canais que podem ser armazenados no pool para cada ponto de extremidade remoto.</span><span class="sxs-lookup"><span data-stu-id="a181e-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="a181e-113">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="a181e-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a181e-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a181e-114">Child Elements</span></span>  
 <span data-ttu-id="a181e-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a181e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a181e-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a181e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a181e-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="a181e-117">Element</span></span>|<span data-ttu-id="a181e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a181e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="a181e-119">Habilita o roteamento de pacotes para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a181e-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a181e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="a181e-120">Remarks</span></span>  
 <span data-ttu-id="a181e-121">As cotas são usadas como um mecanismo de política para evitar o consumo de recursos excessivos.</span><span class="sxs-lookup"><span data-stu-id="a181e-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="a181e-122">Eles impedem ataques de DOS (negação de serviço) que são mal-intencionados ou não intencionais.</span><span class="sxs-lookup"><span data-stu-id="a181e-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="a181e-123">Use este elemento ao definir cotas de canal em um canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="a181e-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="a181e-124">`ChannelPoolSettings`especifica três cotas:</span><span class="sxs-lookup"><span data-stu-id="a181e-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="a181e-125">A `idleTimeout` cota é usada para atenuar ataques de dos (negação de serviço) no servidor que dependem da vinculação de recursos por um longo período de tempo.</span><span class="sxs-lookup"><span data-stu-id="a181e-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="a181e-126">No cliente, a definição do valor correto pode aumentar a confiabilidade da conexão com o serviço.</span><span class="sxs-lookup"><span data-stu-id="a181e-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="a181e-127">O valor padrão é baseado em uma alocação conservadormente modesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="a181e-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="a181e-128">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="a181e-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a181e-129">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="a181e-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="a181e-130">A `leaseTimeout` cota é usada para a integração com balanceadores de carga e para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="a181e-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="a181e-131">O valor padrão é baseado em uma alocação conservadora de recursos.</span><span class="sxs-lookup"><span data-stu-id="a181e-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="a181e-132">Ele é adequado para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="a181e-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a181e-133">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="a181e-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="a181e-134">A `maxOutboundChannelsPerEndpoint` cota define os limites de cache no servidor e no cliente e é usada para melhorar a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="a181e-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="a181e-135">O valor padrão é baseado em uma alocação conservadormente modesto de recursos que é adequada para um ambiente de desenvolvimento e pequenos cenários de instalação.</span><span class="sxs-lookup"><span data-stu-id="a181e-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="a181e-136">Os administradores de serviço devem examinar o valor se uma instalação estiver ficando sem recursos ou se as conexões estiverem sendo limitadas, apesar da disponibilidade de recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="a181e-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a181e-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="a181e-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="a181e-138">Associações</span><span class="sxs-lookup"><span data-stu-id="a181e-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a181e-139">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="a181e-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a181e-140">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a181e-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
