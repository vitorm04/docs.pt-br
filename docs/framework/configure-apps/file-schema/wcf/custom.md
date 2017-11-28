---
title: '&lt;personalizado&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="4a5a2-102">&lt;personalizado&gt;</span><span class="sxs-lookup"><span data-stu-id="4a5a2-102">&lt;custom&gt;</span></span>
<span data-ttu-id="4a5a2-103">Especifica configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="4a5a2-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4a5a2-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-105">\<bindings></span></span>  
<span data-ttu-id="4a5a2-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-106">\<netPeerBinding></span></span>  
<span data-ttu-id="4a5a2-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-107">\<binding></span></span>  
<span data-ttu-id="4a5a2-108">\<resolvedor ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-108">\<resolver></span></span>  
<span data-ttu-id="4a5a2-109">\<personalizado ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5a2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a5a2-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a5a2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a5a2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4a5a2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a5a2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a5a2-113">Attributes</span></span>  
  
|<span data-ttu-id="4a5a2-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="4a5a2-114">Attribute</span></span>|<span data-ttu-id="4a5a2-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a2-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="4a5a2-116">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="4a5a2-117">Uma cadeia de caracteres que especifica o tipo do serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a5a2-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a5a2-118">Child Elements</span></span>  
  
|<span data-ttu-id="4a5a2-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a5a2-119">Element</span></span>|<span data-ttu-id="4a5a2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a5a2-121">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4a5a2-122">Especifica a identidade para os resolvedores de pares personalizado configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="4a5a2-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="4a5a2-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="4a5a2-125">Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipulados pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a5a2-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a5a2-126">Parent Elements</span></span>  
  
|<span data-ttu-id="4a5a2-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a5a2-127">Element</span></span>|<span data-ttu-id="4a5a2-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a5a2-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a5a2-129">\<resolvedor ></span><span class="sxs-lookup"><span data-stu-id="4a5a2-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="4a5a2-130">Um resolvedor de pares que é usado para resolver um par de malha ID para um conjunto de endereços de nó par que representa vários nós que participam na malha.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5a2-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a5a2-131">Remarks</span></span>  
 <span data-ttu-id="4a5a2-132">Este elemento define as configurações básicas para um serviço resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e as configurações de associação específica.</span><span class="sxs-lookup"><span data-stu-id="4a5a2-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="4a5a2-133">Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado para um aplicativo PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="4a5a2-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5a2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5a2-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="4a5a2-135">Resolvedor Peer</span><span class="sxs-lookup"><span data-stu-id="4a5a2-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="4a5a2-136">Adicionando um resolvedor personalizado para um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="4a5a2-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
