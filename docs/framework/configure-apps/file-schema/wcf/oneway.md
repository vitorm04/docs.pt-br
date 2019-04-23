---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: bfda2b9d7b3aa5219a3e4c344347d3b10419a7bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102408"
---
# <a name="oneway"></a><span data-ttu-id="5d4ed-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="5d4ed-101">\<oneWay></span></span>
<span data-ttu-id="5d4ed-102">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="5d4ed-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5d4ed-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5d4ed-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5d4ed-104">\<bindings></span></span>  
<span data-ttu-id="5d4ed-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5d4ed-105">\<customBinding></span></span>  
<span data-ttu-id="5d4ed-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="5d4ed-106">\<binding></span></span>  
<span data-ttu-id="5d4ed-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="5d4ed-107">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4ed-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d4ed-108">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d4ed-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d4ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5d4ed-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d4ed-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d4ed-111">Attributes</span></span>  
  
|<span data-ttu-id="5d4ed-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="5d4ed-112">Attribute</span></span>|<span data-ttu-id="5d4ed-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d4ed-113">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="5d4ed-114">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-114">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="5d4ed-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-115">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="5d4ed-116">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-116">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d4ed-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d4ed-117">Child Elements</span></span>  
  
|<span data-ttu-id="5d4ed-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d4ed-118">Element</span></span>|<span data-ttu-id="5d4ed-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d4ed-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d4ed-120">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="5d4ed-120">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="5d4ed-121">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canal para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-121">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d4ed-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d4ed-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5d4ed-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d4ed-123">Element</span></span>|<span data-ttu-id="5d4ed-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d4ed-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d4ed-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="5d4ed-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5d4ed-126">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d4ed-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d4ed-127">Remarks</span></span>  
 <span data-ttu-id="5d4ed-128">Para habilitar o roteamento de pacotes, uma camada de conversão unidirecional é necessária, que fornece esse elemento.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-128">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="5d4ed-129">Um usuário pode criar uma ligação personalizada que esta associação de camadas em um transporte para torná-lo pacote roteável de reconhecimento de sessão ou de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-129">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="5d4ed-130">Esse elemento também é útil quando você deseja expor métodos unidirecionais de forma mais nativa.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-130">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="5d4ed-131">Mais transformações podem ser aplicadas nessa camada, como Duplex composto e sistema de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="5d4ed-131">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4ed-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d4ed-132">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5d4ed-133">Associações</span><span class="sxs-lookup"><span data-stu-id="5d4ed-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5d4ed-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5d4ed-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5d4ed-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5d4ed-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5d4ed-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5d4ed-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
