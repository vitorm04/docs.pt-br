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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e4b96e1274ad59ae5e63e7935d7408afd069a8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="09949-102">&lt;personalizado&gt;</span><span class="sxs-lookup"><span data-stu-id="09949-102">&lt;custom&gt;</span></span>
<span data-ttu-id="09949-103">Especifica configurações para um serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="09949-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="09949-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="09949-104">\<system.serviceModel></span></span>  
<span data-ttu-id="09949-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="09949-105">\<bindings></span></span>  
<span data-ttu-id="09949-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="09949-106">\<netPeerBinding></span></span>  
<span data-ttu-id="09949-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="09949-107">\<binding></span></span>  
<span data-ttu-id="09949-108">\<resolvedor ></span><span class="sxs-lookup"><span data-stu-id="09949-108">\<resolver></span></span>  
<span data-ttu-id="09949-109">\<personalizado ></span><span class="sxs-lookup"><span data-stu-id="09949-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09949-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09949-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09949-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09949-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09949-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="09949-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09949-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="09949-113">Attributes</span></span>  
  
|<span data-ttu-id="09949-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="09949-114">Attribute</span></span>|<span data-ttu-id="09949-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="09949-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="09949-116">Um URI que especifica o endereço do ponto de extremidade do nó par que hospeda o serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="09949-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="09949-117">Uma cadeia de caracteres que especifica o tipo do serviço resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="09949-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09949-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09949-118">Child Elements</span></span>  
  
|<span data-ttu-id="09949-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="09949-119">Element</span></span>|<span data-ttu-id="09949-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="09949-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09949-121">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="09949-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="09949-122">Especifica a identidade para os resolvedores de pares personalizado configurados com este elemento.</span><span class="sxs-lookup"><span data-stu-id="09949-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="09949-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="09949-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="09949-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="09949-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="09949-125">Uma coleção de cabeçalho de endereço usado para mensagens SOAP manipulados pelo resolvedor de pares personalizado.</span><span class="sxs-lookup"><span data-stu-id="09949-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09949-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09949-126">Parent Elements</span></span>  
  
|<span data-ttu-id="09949-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="09949-127">Element</span></span>|<span data-ttu-id="09949-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="09949-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09949-129">\<resolvedor ></span><span class="sxs-lookup"><span data-stu-id="09949-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="09949-130">Um resolvedor de pares que é usado para resolver um par de malha ID para um conjunto de endereços de nó par que representa vários nós que participam na malha.</span><span class="sxs-lookup"><span data-stu-id="09949-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09949-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="09949-131">Remarks</span></span>  
 <span data-ttu-id="09949-132">Este elemento define as configurações básicas para um serviço resolvedor de pares personalizado, incluindo o endereço do ponto de extremidade do par que hospeda o serviço e as configurações de associação específica.</span><span class="sxs-lookup"><span data-stu-id="09949-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="09949-133">Para obter mais informações sobre a criação de um resolvedor personalizado, consulte [adicionando um resolvedor personalizado para um aplicativo PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span><span class="sxs-lookup"><span data-stu-id="09949-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09949-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09949-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="09949-135">Resolvedor Peer</span><span class="sxs-lookup"><span data-stu-id="09949-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="09949-136">Adicionando um resolvedor personalizado para um aplicativo PeerChannel</span><span class="sxs-lookup"><span data-stu-id="09949-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
