---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 5ff066c32f7d08ec989d6cd04e16c89f0a36f6fa
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675014"
---
# <a name="custom"></a><span data-ttu-id="5312d-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="5312d-101">\<custom></span></span>
<span data-ttu-id="5312d-102">Especifica configurações para um serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="5312d-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="5312d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5312d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5312d-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5312d-104">\<bindings></span></span>  
<span data-ttu-id="5312d-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="5312d-105">\<netPeerBinding></span></span>  
<span data-ttu-id="5312d-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="5312d-106">\<binding></span></span>  
<span data-ttu-id="5312d-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="5312d-107">\<resolver></span></span>  
<span data-ttu-id="5312d-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="5312d-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5312d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5312d-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5312d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5312d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5312d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5312d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5312d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5312d-112">Attributes</span></span>  
  
|<span data-ttu-id="5312d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5312d-113">Attribute</span></span>|<span data-ttu-id="5312d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5312d-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="5312d-115">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="5312d-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="5312d-116">Uma cadeia de caracteres que especifica o tipo de serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="5312d-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5312d-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5312d-117">Child Elements</span></span>  
  
|<span data-ttu-id="5312d-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5312d-118">Element</span></span>|<span data-ttu-id="5312d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5312d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5312d-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="5312d-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5312d-121">Especifica a identidade para os resolvedores de pares personalizados configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="5312d-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="5312d-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="5312d-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="5312d-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="5312d-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="5312d-124">Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipuladas pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="5312d-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5312d-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5312d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5312d-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5312d-126">Element</span></span>|<span data-ttu-id="5312d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5312d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5312d-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="5312d-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="5312d-129">Um resolvedor de pares que é usado para resolver um par de ID de malha para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="5312d-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5312d-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5312d-130">Remarks</span></span>  
 <span data-ttu-id="5312d-131">Este elemento define as configurações básicas para um serviço de resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específica.</span><span class="sxs-lookup"><span data-stu-id="5312d-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="5312d-132">Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5312d-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5312d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5312d-133">See also</span></span>
- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="5312d-134">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="5312d-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="5312d-135">[Adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5312d-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
