---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738795"
---
# <a name="oneway"></a><span data-ttu-id="5e43b-101">> de \<oneWay</span><span class="sxs-lookup"><span data-stu-id="5e43b-101">\<oneWay></span></span>
<span data-ttu-id="5e43b-102">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5e43b-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
<span data-ttu-id="5e43b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e43b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e43b-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5e43b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5e43b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="5e43b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5e43b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="5e43b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5e43b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="5e43b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5e43b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oneWay >**</span><span class="sxs-lookup"><span data-stu-id="5e43b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e43b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e43b-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e43b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e43b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e43b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e43b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e43b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e43b-112">Attributes</span></span>  
  
|<span data-ttu-id="5e43b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e43b-113">Attribute</span></span>|<span data-ttu-id="5e43b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e43b-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="5e43b-115">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5e43b-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="5e43b-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5e43b-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="5e43b-117">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="5e43b-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e43b-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e43b-118">Child Elements</span></span>  
  
|<span data-ttu-id="5e43b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e43b-119">Element</span></span>|<span data-ttu-id="5e43b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e43b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e43b-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="5e43b-121">\<channelPoolSettings></span></span>](channelpoolsettings.md)|<span data-ttu-id="5e43b-122">Um objeto <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> que contém as propriedades do pool de canais para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="5e43b-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e43b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e43b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5e43b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e43b-124">Element</span></span>|<span data-ttu-id="5e43b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e43b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e43b-126">\<binding ></span><span class="sxs-lookup"><span data-stu-id="5e43b-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="5e43b-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5e43b-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e43b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e43b-128">Remarks</span></span>  
 <span data-ttu-id="5e43b-129">Para habilitar o roteamento de pacotes, é necessária uma camada de conversão unidirecional, que esse elemento fornece.</span><span class="sxs-lookup"><span data-stu-id="5e43b-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="5e43b-130">Um usuário pode criar uma associação personalizada que faz a ligação por camadas em um transporte de solicitação ou resposta de sessão para torná-lo roteável.</span><span class="sxs-lookup"><span data-stu-id="5e43b-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="5e43b-131">Esse elemento também é útil quando você deseja expor métodos unidirecionais de maneira mais nativa.</span><span class="sxs-lookup"><span data-stu-id="5e43b-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="5e43b-132">Mais transformações podem ser aplicadas nessa camada, como Composite duplex e mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5e43b-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e43b-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e43b-133">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5e43b-134">Associações</span><span class="sxs-lookup"><span data-stu-id="5e43b-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5e43b-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5e43b-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5e43b-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5e43b-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5e43b-137">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="5e43b-137">\<customBinding></span></span>](custombinding.md)
