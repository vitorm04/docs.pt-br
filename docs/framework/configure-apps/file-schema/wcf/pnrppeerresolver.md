---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181395"
---
# \<pnrpPeerResolver>

<span data-ttu-id="59587-101">Especifica que o resolvedor PNRP (Peer Name Resolution Protocol) deve ser usado como um resolvedor.</span><span class="sxs-lookup"><span data-stu-id="59587-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="59587-102">Esse elemento é opcional porque o PNRP é o resolvedor padrão.</span><span class="sxs-lookup"><span data-stu-id="59587-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="59587-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59587-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59587-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59587-104">Attributes and Elements</span></span>  

 <span data-ttu-id="59587-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59587-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59587-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="59587-106">Attributes</span></span>  
  
|<span data-ttu-id="59587-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="59587-107">Attribute</span></span>|<span data-ttu-id="59587-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="59587-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59587-109">resolvedor</span><span class="sxs-lookup"><span data-stu-id="59587-109">resolverType</span></span>|<span data-ttu-id="59587-110">Uma cadeia de caracteres que especifica o resolvedor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="59587-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="59587-111">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="59587-111">This attribute is optional.</span></span> <span data-ttu-id="59587-112">Se não estiver definido, ou se estiver definido como uma cadeia de caracteres vazia, o PNRP será usado.</span><span class="sxs-lookup"><span data-stu-id="59587-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59587-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59587-113">Child Elements</span></span>  

 <span data-ttu-id="59587-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="59587-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59587-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59587-115">Parent Elements</span></span>  
  
|<span data-ttu-id="59587-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="59587-116">Element</span></span>|<span data-ttu-id="59587-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="59587-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="59587-118">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="59587-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59587-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59587-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="59587-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="59587-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="59587-121">Associações</span><span class="sxs-lookup"><span data-stu-id="59587-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59587-122">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="59587-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="59587-123">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="59587-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="59587-124">Resolvedor peer</span><span class="sxs-lookup"><span data-stu-id="59587-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
