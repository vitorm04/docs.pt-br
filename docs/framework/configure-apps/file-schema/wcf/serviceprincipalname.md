---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936163"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="e2049-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="e2049-101">\<servicePrincipalName></span></span>
<span data-ttu-id="e2049-102">Especifica a identidade de um serviço por seu SPN (nome da entidade de serviço).</span><span class="sxs-lookup"><span data-stu-id="e2049-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="e2049-103">Para obter mais informações sobre como configurar o SPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2049-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e2049-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="e2049-104">\<identity></span></span>  
<span data-ttu-id="e2049-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="e2049-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2049-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2049-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2049-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e2049-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e2049-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="e2049-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2049-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e2049-109">Attributes</span></span>  
  
|<span data-ttu-id="e2049-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="e2049-110">Attribute</span></span>|<span data-ttu-id="e2049-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2049-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2049-112">value</span><span class="sxs-lookup"><span data-stu-id="e2049-112">value</span></span>|<span data-ttu-id="e2049-113">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="e2049-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="e2049-114">Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deverá ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="e2049-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="e2049-115">Uma determinada instância de serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="e2049-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2049-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e2049-116">Child Elements</span></span>  
 <span data-ttu-id="e2049-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e2049-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2049-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e2049-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e2049-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e2049-119">Element</span></span>|<span data-ttu-id="e2049-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2049-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2049-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="e2049-121">\<identity></span></span>](identity.md)|<span data-ttu-id="e2049-122">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="e2049-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2049-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2049-123">Remarks</span></span>  
 <span data-ttu-id="e2049-124">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o SPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e2049-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2049-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2049-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="e2049-126">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e2049-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e2049-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="e2049-127">\<identity></span></span>](identity.md)
