---
title: <certificate> para <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 804600e4eb1612cd8654fc58ec3df28596c1e84d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265032"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="1d554-102">\<certificado > para \<identidade ></span><span class="sxs-lookup"><span data-stu-id="1d554-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="1d554-103">Especifica um certificado X.509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="1d554-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="1d554-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1d554-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="1d554-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="1d554-105">\<identity></span></span>  
<span data-ttu-id="1d554-106">\<certificate></span><span class="sxs-lookup"><span data-stu-id="1d554-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d554-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d554-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d554-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d554-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d554-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d554-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d554-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d554-110">Attributes</span></span>  
  
|<span data-ttu-id="1d554-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1d554-111">Attribute</span></span>|<span data-ttu-id="1d554-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d554-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d554-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="1d554-113">encodedValue</span></span>|<span data-ttu-id="1d554-114">Uma codificação de Base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="1d554-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d554-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d554-115">Child Elements</span></span>  
 <span data-ttu-id="1d554-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1d554-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d554-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d554-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1d554-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d554-118">Element</span></span>|<span data-ttu-id="1d554-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d554-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d554-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="1d554-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1d554-121">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="1d554-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d554-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d554-122">Example</span></span>  
 <span data-ttu-id="1d554-123">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="1d554-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="1d554-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d554-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="1d554-125">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="1d554-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1d554-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="1d554-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
