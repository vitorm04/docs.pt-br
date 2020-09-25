---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 92cd6b280305c223ee125a45724691c5205ce3c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195006"
---
# \<oneWay>

<span data-ttu-id="e306e-101">Habilita o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e306e-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="e306e-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e306e-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e306e-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e306e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e306e-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e306e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e306e-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="e306e-105">Attributes</span></span>  
  
|<span data-ttu-id="e306e-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="e306e-106">Attribute</span></span>|<span data-ttu-id="e306e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e306e-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="e306e-108">Um valor booliano que especifica se o roteamento de pacotes está habilitado.</span><span class="sxs-lookup"><span data-stu-id="e306e-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="e306e-109">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="e306e-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="e306e-110">Um inteiro que especifica o número máximo de canais que podem ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="e306e-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e306e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e306e-111">Child Elements</span></span>  
  
|<span data-ttu-id="e306e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e306e-112">Element</span></span>|<span data-ttu-id="e306e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e306e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="e306e-114">Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canais para o canal atual.</span><span class="sxs-lookup"><span data-stu-id="e306e-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e306e-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e306e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e306e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="e306e-116">Element</span></span>|<span data-ttu-id="e306e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e306e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e306e-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e306e-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e306e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="e306e-119">Remarks</span></span>  

 <span data-ttu-id="e306e-120">Para habilitar o roteamento de pacotes, é necessária uma camada de conversão unidirecional, que esse elemento fornece.</span><span class="sxs-lookup"><span data-stu-id="e306e-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="e306e-121">Um usuário pode criar uma associação personalizada que faz a ligação por camadas em um transporte de solicitação ou resposta de sessão para torná-lo roteável.</span><span class="sxs-lookup"><span data-stu-id="e306e-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="e306e-122">Esse elemento também é útil quando você deseja expor métodos unidirecionais de maneira mais nativa.</span><span class="sxs-lookup"><span data-stu-id="e306e-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="e306e-123">Mais transformações podem ser aplicadas nessa camada, como Composite duplex e mensagens confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e306e-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e306e-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="e306e-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e306e-125">Associações</span><span class="sxs-lookup"><span data-stu-id="e306e-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e306e-126">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e306e-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e306e-127">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e306e-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
