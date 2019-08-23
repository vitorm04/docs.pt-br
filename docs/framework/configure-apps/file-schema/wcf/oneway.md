---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f4a9422f4385e37a61ec85d680fcf7743a57bc0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932940"
---
# <a name="oneway"></a><span data-ttu-id="4ea1b-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="4ea1b-101">\<oneWay></span></span>
<span data-ttu-id="4ea1b-102">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="4ea1b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ea1b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4ea1b-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4ea1b-104">\<bindings></span></span>  
<span data-ttu-id="4ea1b-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4ea1b-105">\<customBinding></span></span>  
<span data-ttu-id="4ea1b-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="4ea1b-106">\<binding></span></span>  
<span data-ttu-id="4ea1b-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="4ea1b-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea1b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ea1b-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ea1b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4ea1b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4ea1b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ea1b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4ea1b-111">Attributes</span></span>  
  
|<span data-ttu-id="4ea1b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="4ea1b-112">Attribute</span></span>|<span data-ttu-id="4ea1b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ea1b-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="4ea1b-114">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="4ea1b-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="4ea1b-116">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ea1b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4ea1b-117">Child Elements</span></span>  
  
|<span data-ttu-id="4ea1b-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ea1b-118">Element</span></span>|<span data-ttu-id="4ea1b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ea1b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea1b-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="4ea1b-120">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="4ea1b-121">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canais para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ea1b-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4ea1b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4ea1b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="4ea1b-123">Element</span></span>|<span data-ttu-id="4ea1b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ea1b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea1b-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="4ea1b-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4ea1b-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ea1b-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ea1b-127">Remarks</span></span>  
 <span data-ttu-id="4ea1b-128">Para habilitar o roteamento de pacotes, é necessária uma camada de conversão unidirecional, que esse elemento fornece.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="4ea1b-129">Um usuário pode criar uma associação personalizada que faz a ligação por camadas em um transporte de solicitação ou resposta de sessão para torná-lo roteável.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="4ea1b-130">Esse elemento também é útil quando você deseja expor métodos unidirecionais de maneira mais nativa.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="4ea1b-131">Mais transformações podem ser aplicadas nessa camada, como Composite duplex e mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4ea1b-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea1b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ea1b-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4ea1b-133">Associações</span><span class="sxs-lookup"><span data-stu-id="4ea1b-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4ea1b-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="4ea1b-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4ea1b-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="4ea1b-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4ea1b-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4ea1b-136">\<customBinding></span></span>](custombinding.md)
