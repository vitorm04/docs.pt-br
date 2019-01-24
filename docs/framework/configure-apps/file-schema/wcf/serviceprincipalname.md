---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 5d65b5956491e30066ece54a48374f1d7014552e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657567"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="9a4d1-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="9a4d1-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="9a4d1-103">Especifica a identidade de um serviço por seu serviço Nome Principal (SPN).</span><span class="sxs-lookup"><span data-stu-id="9a4d1-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="9a4d1-104">Para obter mais informações sobre como definir o SPN, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9a4d1-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="9a4d1-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="9a4d1-105">\<identity></span></span>  
<span data-ttu-id="9a4d1-106">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="9a4d1-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a4d1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a4d1-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a4d1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a4d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9a4d1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a4d1-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a4d1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a4d1-110">Attributes</span></span>  
  
|<span data-ttu-id="9a4d1-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9a4d1-111">Attribute</span></span>|<span data-ttu-id="9a4d1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a4d1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a4d1-113">Valor </span><span class="sxs-lookup"><span data-stu-id="9a4d1-113">value</span></span>|<span data-ttu-id="9a4d1-114">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="9a4d1-115">Se você instalar várias instâncias de um serviço em computadores em toda a floresta, cada instância deve ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="9a4d1-116">Uma instância de determinado serviço pode ter vários SPNs, se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a4d1-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a4d1-117">Child Elements</span></span>  
 <span data-ttu-id="9a4d1-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a4d1-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a4d1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9a4d1-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a4d1-120">Element</span></span>|<span data-ttu-id="9a4d1-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a4d1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a4d1-122">\<identity></span><span class="sxs-lookup"><span data-stu-id="9a4d1-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9a4d1-123">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a4d1-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a4d1-124">Remarks</span></span>  
 <span data-ttu-id="9a4d1-125">Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade usa o SPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9a4d1-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a4d1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a4d1-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="9a4d1-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="9a4d1-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9a4d1-128">\<identity></span><span class="sxs-lookup"><span data-stu-id="9a4d1-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
