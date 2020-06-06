---
title: <certificate> para <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850018"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="c9a8b-102">\<certificate> para \<identity></span><span class="sxs-lookup"><span data-stu-id="c9a8b-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="c9a8b-103">Especifica um certificado X. 509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="c9a8b-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c9a8b-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="c9a8b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9a8b-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9a8b-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9a8b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c9a8b-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9a8b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9a8b-108">Attributes</span></span>  
  
|<span data-ttu-id="c9a8b-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a8b-109">Attribute</span></span>|<span data-ttu-id="c9a8b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9a8b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9a8b-111">codificado</span><span class="sxs-lookup"><span data-stu-id="c9a8b-111">encodedValue</span></span>|<span data-ttu-id="c9a8b-112">Uma codificação base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9a8b-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9a8b-113">Child Elements</span></span>  
 <span data-ttu-id="c9a8b-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9a8b-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9a8b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c9a8b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9a8b-116">Element</span></span>|<span data-ttu-id="c9a8b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9a8b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c9a8b-118">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9a8b-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9a8b-119">Example</span></span>  
 <span data-ttu-id="c9a8b-120">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="c9a8b-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9a8b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9a8b-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="c9a8b-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="c9a8b-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
