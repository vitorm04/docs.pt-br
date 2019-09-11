---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854999"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="3c305-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="3c305-101">\<servicePrincipalName></span></span>
<span data-ttu-id="3c305-102">Especifica a identidade de um serviço por seu SPN (nome da entidade de serviço).</span><span class="sxs-lookup"><span data-stu-id="3c305-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="3c305-103">Para obter mais informações sobre como configurar o SPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3c305-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="3c305-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c305-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3c305-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3c305-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3c305-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="3c305-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="3c305-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="3c305-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="3c305-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="3c305-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="3c305-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de servicePrincipalName**</span><span class="sxs-lookup"><span data-stu-id="3c305-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c305-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c305-110">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c305-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c305-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3c305-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c305-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c305-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c305-113">Attributes</span></span>  
  
|<span data-ttu-id="3c305-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3c305-114">Attribute</span></span>|<span data-ttu-id="3c305-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c305-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c305-116">value</span><span class="sxs-lookup"><span data-stu-id="3c305-116">value</span></span>|<span data-ttu-id="3c305-117">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="3c305-117">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="3c305-118">Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deverá ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="3c305-118">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="3c305-119">Uma determinada instância de serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="3c305-119">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c305-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3c305-120">Child Elements</span></span>  
 <span data-ttu-id="3c305-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3c305-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c305-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c305-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3c305-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c305-123">Element</span></span>|<span data-ttu-id="3c305-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c305-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c305-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="3c305-125">\<identity></span></span>](identity.md)|<span data-ttu-id="3c305-126">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="3c305-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c305-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c305-127">Remarks</span></span>  
 <span data-ttu-id="3c305-128">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o SPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3c305-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c305-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c305-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="3c305-130">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="3c305-130">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3c305-131">\<identity></span><span class="sxs-lookup"><span data-stu-id="3c305-131">\<identity></span></span>](identity.md)
