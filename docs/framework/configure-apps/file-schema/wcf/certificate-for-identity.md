---
title: <certificate>fins<identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850018"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="ff9e6-102">\<> de certificado \<para > de identidade</span><span class="sxs-lookup"><span data-stu-id="ff9e6-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="ff9e6-103">Especifica um certificado X. 509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="ff9e6-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ff9e6-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="ff9e6-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff9e6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff9e6-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ff9e6-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff9e6-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="ff9e6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="ff9e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="ff9e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="ff9e6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="ff9e6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="ff9e6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificado**</span><span class="sxs-lookup"><span data-stu-id="ff9e6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9e6-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff9e6-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff9e6-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff9e6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ff9e6-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff9e6-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff9e6-114">Attributes</span></span>  
  
|<span data-ttu-id="ff9e6-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff9e6-115">Attribute</span></span>|<span data-ttu-id="ff9e6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff9e6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff9e6-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="ff9e6-117">encodedValue</span></span>|<span data-ttu-id="ff9e6-118">Uma codificação base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff9e6-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff9e6-119">Child Elements</span></span>  
 <span data-ttu-id="ff9e6-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff9e6-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff9e6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ff9e6-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff9e6-122">Element</span></span>|<span data-ttu-id="ff9e6-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff9e6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff9e6-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="ff9e6-124">\<identity></span></span>](identity.md)|<span data-ttu-id="ff9e6-125">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff9e6-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff9e6-126">Example</span></span>  
 <span data-ttu-id="ff9e6-127">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="ff9e6-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="ff9e6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff9e6-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="ff9e6-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ff9e6-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ff9e6-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="ff9e6-130">\<identity></span></span>](identity.md)
