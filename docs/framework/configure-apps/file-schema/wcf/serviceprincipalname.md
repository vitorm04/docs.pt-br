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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e472c7fcfd57341074489a75f7954be38291523b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="39548-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="39548-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="39548-103">Especifica a identidade de um serviço por seu serviço Nome Principal (SPN).</span><span class="sxs-lookup"><span data-stu-id="39548-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="39548-104">Para obter mais informações sobre como configurar o SPN, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="39548-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="39548-105">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="39548-105">\<identity></span></span>  
<span data-ttu-id="39548-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="39548-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39548-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39548-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39548-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39548-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39548-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="39548-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39548-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="39548-110">Attributes</span></span>  
  
|<span data-ttu-id="39548-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="39548-111">Attribute</span></span>|<span data-ttu-id="39548-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="39548-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39548-113">Valor </span><span class="sxs-lookup"><span data-stu-id="39548-113">value</span></span>|<span data-ttu-id="39548-114">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="39548-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="39548-115">Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deve ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="39548-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="39548-116">Uma instância de determinado serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="39548-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39548-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39548-117">Child Elements</span></span>  
 <span data-ttu-id="39548-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="39548-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39548-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39548-119">Parent Elements</span></span>  
  
|<span data-ttu-id="39548-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="39548-120">Element</span></span>|<span data-ttu-id="39548-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="39548-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39548-122">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="39548-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="39548-123">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="39548-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39548-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="39548-124">Remarks</span></span>  
 <span data-ttu-id="39548-125">Seguro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] cliente que se conecta a um ponto de extremidade com esta identidade usa o SPN ao executar a autenticação de SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="39548-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39548-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39548-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="39548-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="39548-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="39548-128">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="39548-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
