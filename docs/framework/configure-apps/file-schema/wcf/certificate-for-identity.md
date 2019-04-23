---
title: <certificate> para <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 76bdcb40d5016d7fcbff6c0d9769819f710065fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205830"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="5725c-102">\<certificado > para \<identidade ></span><span class="sxs-lookup"><span data-stu-id="5725c-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="5725c-103">Especifica um certificado X.509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="5725c-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="5725c-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5725c-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="5725c-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="5725c-105">\<identity></span></span>  
<span data-ttu-id="5725c-106">\<certificate></span><span class="sxs-lookup"><span data-stu-id="5725c-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5725c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5725c-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5725c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5725c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5725c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5725c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5725c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5725c-110">Attributes</span></span>  
  
|<span data-ttu-id="5725c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5725c-111">Attribute</span></span>|<span data-ttu-id="5725c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5725c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5725c-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="5725c-113">encodedValue</span></span>|<span data-ttu-id="5725c-114">Uma codificação de Base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="5725c-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5725c-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5725c-115">Child Elements</span></span>  
 <span data-ttu-id="5725c-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5725c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5725c-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5725c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5725c-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5725c-118">Element</span></span>|<span data-ttu-id="5725c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5725c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5725c-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="5725c-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5725c-121">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="5725c-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5725c-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5725c-122">Example</span></span>  
 <span data-ttu-id="5725c-123">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="5725c-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="5725c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5725c-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="5725c-125">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5725c-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5725c-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="5725c-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
