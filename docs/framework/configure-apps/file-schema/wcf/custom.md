---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400459"
---
# \<custom>
<span data-ttu-id="0fbaa-101">Especifica as configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="0fbaa-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fbaa-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fbaa-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0fbaa-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0fbaa-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fbaa-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="0fbaa-105">Attributes</span></span>  
  
|<span data-ttu-id="0fbaa-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="0fbaa-106">Attribute</span></span>|<span data-ttu-id="0fbaa-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fbaa-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="0fbaa-108">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="0fbaa-109">Uma cadeia de caracteres que especifica o tipo do serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fbaa-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0fbaa-110">Child Elements</span></span>  
  
|<span data-ttu-id="0fbaa-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0fbaa-111">Element</span></span>|<span data-ttu-id="0fbaa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fbaa-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="0fbaa-113">Especifica a identidade para resolvedores de pares personalizados configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="0fbaa-114">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement> .</span><span class="sxs-lookup"><span data-stu-id="0fbaa-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="0fbaa-115">Uma coleção de cabeçalho de endereço usada para mensagens SOAP tratadas pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fbaa-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0fbaa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0fbaa-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0fbaa-117">Element</span></span>|<span data-ttu-id="0fbaa-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fbaa-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="0fbaa-119">Um resolvedor de pares que é usado para resolver uma ID de malha de mesmo nível para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fbaa-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fbaa-120">Remarks</span></span>  
 <span data-ttu-id="0fbaa-121">Esse elemento define as configurações básicas para um serviço resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específicas.</span><span class="sxs-lookup"><span data-stu-id="0fbaa-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="0fbaa-122">Para obter mais informações sobre como criar um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0fbaa-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fbaa-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="0fbaa-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="0fbaa-124">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="0fbaa-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="0fbaa-125">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0fbaa-125">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
