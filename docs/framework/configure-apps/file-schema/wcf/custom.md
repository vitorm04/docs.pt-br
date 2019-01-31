---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 2b268d9d040bbeed2b3563783226f7ca8c18e3b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254282"
---
# <a name="custom"></a><span data-ttu-id="2a8ca-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="2a8ca-101">\<custom></span></span>
<span data-ttu-id="2a8ca-102">Especifica configurações para um serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="2a8ca-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a8ca-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2a8ca-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2a8ca-104">\<bindings></span></span>  
<span data-ttu-id="2a8ca-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="2a8ca-105">\<netPeerBinding></span></span>  
<span data-ttu-id="2a8ca-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="2a8ca-106">\<binding></span></span>  
<span data-ttu-id="2a8ca-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="2a8ca-107">\<resolver></span></span>  
<span data-ttu-id="2a8ca-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="2a8ca-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a8ca-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a8ca-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a8ca-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a8ca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a8ca-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a8ca-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a8ca-112">Attributes</span></span>  
  
|<span data-ttu-id="2a8ca-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a8ca-113">Attribute</span></span>|<span data-ttu-id="2a8ca-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8ca-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="2a8ca-115">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="2a8ca-116">Uma cadeia de caracteres que especifica o tipo de serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a8ca-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a8ca-117">Child Elements</span></span>  
  
|<span data-ttu-id="2a8ca-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a8ca-118">Element</span></span>|<span data-ttu-id="2a8ca-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8ca-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a8ca-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="2a8ca-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2a8ca-121">Especifica a identidade para os resolvedores de pares personalizados configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="2a8ca-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="2a8ca-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="2a8ca-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2a8ca-124">Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipuladas pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a8ca-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a8ca-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2a8ca-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a8ca-126">Element</span></span>|<span data-ttu-id="2a8ca-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a8ca-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a8ca-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="2a8ca-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="2a8ca-129">Um resolvedor de pares que é usado para resolver um par de ID de malha para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a8ca-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a8ca-130">Remarks</span></span>  
 <span data-ttu-id="2a8ca-131">Este elemento define as configurações básicas para um serviço de resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específica.</span><span class="sxs-lookup"><span data-stu-id="2a8ca-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="2a8ca-132">Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="2a8ca-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a8ca-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a8ca-133">See also</span></span>
- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="2a8ca-134">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="2a8ca-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="2a8ca-135">Adicionando um resolvedor personalizado a um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="2a8ca-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
