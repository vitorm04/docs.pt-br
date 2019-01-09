---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 1978c898039a6ff9ab3303427951c214cde96e24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145739"
---
# <a name="ltcustomgt"></a><span data-ttu-id="99458-102">&lt;custom&gt;</span><span class="sxs-lookup"><span data-stu-id="99458-102">&lt;custom&gt;</span></span>
<span data-ttu-id="99458-103">Especifica configurações para um serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="99458-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="99458-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99458-104">\<system.serviceModel></span></span>  
<span data-ttu-id="99458-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="99458-105">\<bindings></span></span>  
<span data-ttu-id="99458-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="99458-106">\<netPeerBinding></span></span>  
<span data-ttu-id="99458-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="99458-107">\<binding></span></span>  
<span data-ttu-id="99458-108">\<resolver></span><span class="sxs-lookup"><span data-stu-id="99458-108">\<resolver></span></span>  
<span data-ttu-id="99458-109">\<custom></span><span class="sxs-lookup"><span data-stu-id="99458-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99458-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99458-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99458-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99458-111">Attributes and Elements</span></span>  
 <span data-ttu-id="99458-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="99458-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99458-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="99458-113">Attributes</span></span>  
  
|<span data-ttu-id="99458-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="99458-114">Attribute</span></span>|<span data-ttu-id="99458-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="99458-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="99458-116">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço de resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="99458-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="99458-117">Uma cadeia de caracteres que especifica o tipo de serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="99458-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99458-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99458-118">Child Elements</span></span>  
  
|<span data-ttu-id="99458-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="99458-119">Element</span></span>|<span data-ttu-id="99458-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="99458-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99458-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="99458-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="99458-122">Especifica a identidade para os resolvedores de pares personalizados configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="99458-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="99458-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="99458-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="99458-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="99458-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="99458-125">Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipuladas pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="99458-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99458-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99458-126">Parent Elements</span></span>  
  
|<span data-ttu-id="99458-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="99458-127">Element</span></span>|<span data-ttu-id="99458-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="99458-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99458-129">\<resolver></span><span class="sxs-lookup"><span data-stu-id="99458-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="99458-130">Um resolvedor de pares que é usado para resolver um par de ID de malha para um conjunto de endereços de nó par que representa vários nós que participam da malha.</span><span class="sxs-lookup"><span data-stu-id="99458-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99458-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="99458-131">Remarks</span></span>  
 <span data-ttu-id="99458-132">Este elemento define as configurações básicas para um serviço de resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e quaisquer configurações de associação específica.</span><span class="sxs-lookup"><span data-stu-id="99458-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="99458-133">Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado a um aplicativo PeerChannel](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="99458-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99458-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99458-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="99458-135">Resolvedores pares</span><span class="sxs-lookup"><span data-stu-id="99458-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="99458-136">Adicionando um resolvedor personalizado a um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="99458-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
