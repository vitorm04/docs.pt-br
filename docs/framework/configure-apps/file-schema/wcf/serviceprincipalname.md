---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 75e95bcbaee229f19bdfdd119b548ed612f4ddaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204400"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="c18ac-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="c18ac-101">\<servicePrincipalName></span></span>
<span data-ttu-id="c18ac-102">Especifica a identidade de um serviço por seu serviço Nome Principal (SPN).</span><span class="sxs-lookup"><span data-stu-id="c18ac-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="c18ac-103">Para obter mais informações sobre como definir o SPN, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c18ac-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c18ac-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="c18ac-104">\<identity></span></span>  
<span data-ttu-id="c18ac-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="c18ac-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18ac-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c18ac-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c18ac-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c18ac-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c18ac-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="c18ac-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c18ac-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c18ac-109">Attributes</span></span>  
  
|<span data-ttu-id="c18ac-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c18ac-110">Attribute</span></span>|<span data-ttu-id="c18ac-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18ac-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c18ac-112">Valor </span><span class="sxs-lookup"><span data-stu-id="c18ac-112">value</span></span>|<span data-ttu-id="c18ac-113">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="c18ac-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="c18ac-114">Se você instalar várias instâncias de um serviço em computadores em toda a floresta, cada instância deve ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="c18ac-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="c18ac-115">Uma instância de determinado serviço pode ter vários SPNs, se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c18ac-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c18ac-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c18ac-116">Child Elements</span></span>  
 <span data-ttu-id="c18ac-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c18ac-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c18ac-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c18ac-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c18ac-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c18ac-119">Element</span></span>|<span data-ttu-id="c18ac-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18ac-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c18ac-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="c18ac-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c18ac-122">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c18ac-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c18ac-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c18ac-123">Remarks</span></span>  
 <span data-ttu-id="c18ac-124">Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade usa o SPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c18ac-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18ac-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c18ac-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="c18ac-126">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="c18ac-126">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c18ac-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="c18ac-127">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
