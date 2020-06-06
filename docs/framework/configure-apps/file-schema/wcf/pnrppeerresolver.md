---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738772"
---
# \<pnrpPeerResolver>
<span data-ttu-id="f2c01-101">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="f2c01-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="f2c01-102">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="f2c01-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="f2c01-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2c01-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2c01-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f2c01-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f2c01-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f2c01-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2c01-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="f2c01-106">Attributes</span></span>  
  
|<span data-ttu-id="f2c01-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c01-107">Attribute</span></span>|<span data-ttu-id="f2c01-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2c01-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2c01-109">resolvedor</span><span class="sxs-lookup"><span data-stu-id="f2c01-109">resolverType</span></span>|<span data-ttu-id="f2c01-110">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f2c01-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="f2c01-111">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="f2c01-111">This attribute is optional.</span></span> <span data-ttu-id="f2c01-112">Se não estiver definido, ou se estiver definido como uma cadeia de caracteres vazia, o PNRP será usado.</span><span class="sxs-lookup"><span data-stu-id="f2c01-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2c01-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f2c01-113">Child Elements</span></span>  
 <span data-ttu-id="f2c01-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f2c01-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2c01-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f2c01-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f2c01-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2c01-116">Element</span></span>|<span data-ttu-id="f2c01-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2c01-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f2c01-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f2c01-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2c01-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2c01-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f2c01-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2c01-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f2c01-121">Associações</span><span class="sxs-lookup"><span data-stu-id="f2c01-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2c01-122">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="f2c01-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f2c01-123">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f2c01-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f2c01-124">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="f2c01-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
