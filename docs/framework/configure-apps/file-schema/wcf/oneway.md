---
title: '&lt;oneWay&gt;'
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: c909bce5b54976a215a59ca8fd9f097f574acd80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600291"
---
# <a name="ltonewaygt"></a><span data-ttu-id="86db5-102">&lt;oneWay&gt;</span><span class="sxs-lookup"><span data-stu-id="86db5-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="86db5-103">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="86db5-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="86db5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="86db5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="86db5-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="86db5-105">\<bindings></span></span>  
<span data-ttu-id="86db5-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="86db5-106">\<customBinding></span></span>  
<span data-ttu-id="86db5-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="86db5-107">\<binding></span></span>  
<span data-ttu-id="86db5-108">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="86db5-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86db5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86db5-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86db5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86db5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86db5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="86db5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86db5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="86db5-112">Attributes</span></span>  
  
|<span data-ttu-id="86db5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="86db5-113">Attribute</span></span>|<span data-ttu-id="86db5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="86db5-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="86db5-115">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="86db5-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="86db5-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="86db5-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="86db5-117">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="86db5-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86db5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="86db5-118">Child Elements</span></span>  
  
|<span data-ttu-id="86db5-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="86db5-119">Element</span></span>|<span data-ttu-id="86db5-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="86db5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86db5-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="86db5-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="86db5-122">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canal para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="86db5-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86db5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="86db5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="86db5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="86db5-124">Element</span></span>|<span data-ttu-id="86db5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="86db5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86db5-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="86db5-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="86db5-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="86db5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86db5-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="86db5-128">Remarks</span></span>  
 <span data-ttu-id="86db5-129">Para habilitar o roteamento de pacotes, uma camada de conversão unidirecional é necessária, que fornece esse elemento.</span><span class="sxs-lookup"><span data-stu-id="86db5-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="86db5-130">Um usuário pode criar uma ligação personalizada que esta associação de camadas em um transporte para torná-lo pacote roteável de reconhecimento de sessão ou de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="86db5-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="86db5-131">Esse elemento também é útil quando você deseja expor métodos unidirecionais de forma mais nativa.</span><span class="sxs-lookup"><span data-stu-id="86db5-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="86db5-132">Mais transformações podem ser aplicadas nessa camada, como Duplex composto e sistema de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="86db5-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86db5-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86db5-133">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="86db5-134">Associações</span><span class="sxs-lookup"><span data-stu-id="86db5-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="86db5-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="86db5-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="86db5-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="86db5-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="86db5-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="86db5-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
