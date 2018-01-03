---
title: '&lt;Unidirecional&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="14367-102">&lt;Unidirecional&gt;</span><span class="sxs-lookup"><span data-stu-id="14367-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="14367-103">Permite que o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="14367-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="14367-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="14367-104">\<system.serviceModel></span></span>  
<span data-ttu-id="14367-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="14367-105">\<bindings></span></span>  
<span data-ttu-id="14367-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="14367-106">\<customBinding></span></span>  
<span data-ttu-id="14367-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="14367-107">\<binding></span></span>  
<span data-ttu-id="14367-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="14367-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14367-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14367-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14367-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="14367-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14367-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="14367-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14367-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="14367-112">Attributes</span></span>  
  
|<span data-ttu-id="14367-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="14367-113">Attribute</span></span>|<span data-ttu-id="14367-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="14367-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="14367-115">Um valor booleano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="14367-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="14367-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="14367-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="14367-117">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="14367-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14367-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="14367-118">Child Elements</span></span>  
  
|<span data-ttu-id="14367-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="14367-119">Element</span></span>|<span data-ttu-id="14367-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="14367-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14367-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="14367-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="14367-122">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canal para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="14367-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14367-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="14367-123">Parent Elements</span></span>  
  
|<span data-ttu-id="14367-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="14367-124">Element</span></span>|<span data-ttu-id="14367-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="14367-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14367-126">\<associação ></span><span class="sxs-lookup"><span data-stu-id="14367-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="14367-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="14367-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14367-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="14367-128">Remarks</span></span>  
 <span data-ttu-id="14367-129">Para habilitar o roteamento de pacotes, uma camada de conversão unidirecional é necessária, que fornece este elemento.</span><span class="sxs-lookup"><span data-stu-id="14367-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="14367-130">Um usuário pode criar uma associação personalizada que camadas essa ligação por um transporte de reconhecimento de sessão ou de solicitação-resposta para torná-lo pacote roteável.</span><span class="sxs-lookup"><span data-stu-id="14367-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="14367-131">Esse elemento também é útil quando você deseja expor métodos unidirecionais de forma mais nativo.</span><span class="sxs-lookup"><span data-stu-id="14367-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="14367-132">Mais transformações podem ser aplicadas por essa camada, como Duplex compostos e sistema de mensagens confiável.</span><span class="sxs-lookup"><span data-stu-id="14367-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14367-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14367-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="14367-134">Associações</span><span class="sxs-lookup"><span data-stu-id="14367-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="14367-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="14367-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="14367-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="14367-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="14367-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="14367-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
