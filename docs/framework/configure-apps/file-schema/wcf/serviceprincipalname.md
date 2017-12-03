---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b734a095f0c9ea9ad1bd6e78f3ef4264f4f2317e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="5764a-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="5764a-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="5764a-103">Especifica a identidade de um serviço por seu serviço Nome Principal (SPN).</span><span class="sxs-lookup"><span data-stu-id="5764a-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="5764a-104">Para obter mais informações sobre como configurar o SPN, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5764a-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="5764a-105">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="5764a-105">\<identity></span></span>  
<span data-ttu-id="5764a-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="5764a-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5764a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5764a-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5764a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5764a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5764a-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="5764a-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5764a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5764a-110">Attributes</span></span>  
  
|<span data-ttu-id="5764a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5764a-111">Attribute</span></span>|<span data-ttu-id="5764a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5764a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5764a-113">Valor </span><span class="sxs-lookup"><span data-stu-id="5764a-113">value</span></span>|<span data-ttu-id="5764a-114">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="5764a-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="5764a-115">Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deve ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="5764a-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="5764a-116">Uma instância de determinado serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5764a-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5764a-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5764a-117">Child Elements</span></span>  
 <span data-ttu-id="5764a-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5764a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5764a-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5764a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5764a-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="5764a-120">Element</span></span>|<span data-ttu-id="5764a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5764a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5764a-122">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="5764a-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5764a-123">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="5764a-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5764a-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="5764a-124">Remarks</span></span>  
 <span data-ttu-id="5764a-125">Seguro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] cliente que se conecta a um ponto de extremidade com esta identidade usa o SPN ao executar a autenticação de SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5764a-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5764a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5764a-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="5764a-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5764a-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5764a-128">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="5764a-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
