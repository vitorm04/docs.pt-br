---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 0d03844a58de5b4af93f276de75c88af6efed3f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153788"
---
# \<servicePrincipalName>

<span data-ttu-id="ba06c-101">Especifica a identidade de um serviço por seu SPN (nome da entidade de serviço).</span><span class="sxs-lookup"><span data-stu-id="ba06c-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="ba06c-102">Para obter mais informações sobre como configurar o SPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ba06c-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="ba06c-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba06c-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba06c-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba06c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ba06c-105">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba06c-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba06c-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba06c-106">Attributes</span></span>  
  
|<span data-ttu-id="ba06c-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba06c-107">Attribute</span></span>|<span data-ttu-id="ba06c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba06c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba06c-109">value</span><span class="sxs-lookup"><span data-stu-id="ba06c-109">value</span></span>|<span data-ttu-id="ba06c-110">O nome pelo qual um cliente identifica exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="ba06c-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="ba06c-111">Se você instalar várias instâncias de um serviço em computadores em uma floresta, cada instância deverá ter seu próprio SPN.</span><span class="sxs-lookup"><span data-stu-id="ba06c-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="ba06c-112">Uma determinada instância de serviço pode ter vários SPNs se houver vários nomes que os clientes podem usar para autenticação.</span><span class="sxs-lookup"><span data-stu-id="ba06c-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba06c-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba06c-113">Child Elements</span></span>  

 <span data-ttu-id="ba06c-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ba06c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba06c-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba06c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ba06c-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba06c-116">Element</span></span>|<span data-ttu-id="ba06c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba06c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="ba06c-118">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="ba06c-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba06c-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba06c-119">Remarks</span></span>  

 <span data-ttu-id="ba06c-120">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o SPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ba06c-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba06c-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ba06c-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="ba06c-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="ba06c-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
