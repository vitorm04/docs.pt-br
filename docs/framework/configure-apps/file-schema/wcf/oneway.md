---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: f12969d8b752e54916b45c3d0e64f114971b8944
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397660"
---
# <a name="oneway"></a><span data-ttu-id="e9f7f-101">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="e9f7f-101">\<oneWay></span></span>
<span data-ttu-id="e9f7f-102">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="e9f7f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9f7f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9f7f-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9f7f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9f7f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e9f7f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e9f7f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e9f7f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e9f7f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="e9f7f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e9f7f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oneWay >**</span><span class="sxs-lookup"><span data-stu-id="e9f7f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f7f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9f7f-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9f7f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e9f7f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9f7f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9f7f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9f7f-112">Attributes</span></span>  
  
|<span data-ttu-id="e9f7f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e9f7f-113">Attribute</span></span>|<span data-ttu-id="e9f7f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f7f-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="e9f7f-115">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="e9f7f-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="e9f7f-117">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9f7f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e9f7f-118">Child Elements</span></span>  
  
|<span data-ttu-id="e9f7f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f7f-119">Element</span></span>|<span data-ttu-id="e9f7f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f7f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9f7f-121">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="e9f7f-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="e9f7f-122">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canais para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9f7f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e9f7f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9f7f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f7f-124">Element</span></span>|<span data-ttu-id="e9f7f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f7f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9f7f-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9f7f-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e9f7f-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f7f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9f7f-128">Remarks</span></span>  
 <span data-ttu-id="e9f7f-129">Para habilitar o roteamento de pacotes, é necessária uma camada de conversão unidirecional, que esse elemento fornece.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="e9f7f-130">Um usuário pode criar uma associação personalizada que faz a ligação por camadas em um transporte de solicitação ou resposta de sessão para torná-lo roteável.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="e9f7f-131">Esse elemento também é útil quando você deseja expor métodos unidirecionais de maneira mais nativa.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="e9f7f-132">Mais transformações podem ser aplicadas nessa camada, como Composite duplex e mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e9f7f-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f7f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9f7f-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e9f7f-134">Associações</span><span class="sxs-lookup"><span data-stu-id="e9f7f-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9f7f-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e9f7f-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9f7f-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e9f7f-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e9f7f-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e9f7f-137">\<customBinding></span></span>](custombinding.md)
