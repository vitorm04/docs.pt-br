---
title: '&lt;certificado&gt; de &lt;identidade&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="0a4e7-102">&lt;certificado&gt; de &lt;identidade&gt;</span><span class="sxs-lookup"><span data-stu-id="0a4e7-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="0a4e7-103">Especifica um certificado x. 509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="0a4e7-104">Para obter mais informações sobre como definir o valor do elemento, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0a4e7-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="0a4e7-105">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="0a4e7-105">\<identity></span></span>  
<span data-ttu-id="0a4e7-106">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="0a4e7-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a4e7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a4e7-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a4e7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a4e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a4e7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a4e7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a4e7-110">Attributes</span></span>  
  
|<span data-ttu-id="0a4e7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0a4e7-111">Attribute</span></span>|<span data-ttu-id="0a4e7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4e7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a4e7-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="0a4e7-113">encodedValue</span></span>|<span data-ttu-id="0a4e7-114">Uma codificação Base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a4e7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a4e7-115">Child Elements</span></span>  
 <span data-ttu-id="0a4e7-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a4e7-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a4e7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0a4e7-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a4e7-118">Element</span></span>|<span data-ttu-id="0a4e7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4e7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a4e7-120">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="0a4e7-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0a4e7-121">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a4e7-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a4e7-122">Example</span></span>  
 <span data-ttu-id="0a4e7-123">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="0a4e7-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a4e7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a4e7-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="0a4e7-125">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="0a4e7-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="0a4e7-126">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="0a4e7-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
