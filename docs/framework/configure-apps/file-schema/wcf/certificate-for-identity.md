---
title: <certificate> para <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 24c39b5efaee7f8db12088d272efeb3783efab04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198854"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="18a00-102">\<certificate> para \<identity></span><span class="sxs-lookup"><span data-stu-id="18a00-102">\<certificate> for \<identity></span></span>

<span data-ttu-id="18a00-103">Especifica um certificado X. 509 usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="18a00-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="18a00-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="18a00-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="18a00-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18a00-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18a00-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="18a00-106">Attributes and Elements</span></span>  

 <span data-ttu-id="18a00-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="18a00-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18a00-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="18a00-108">Attributes</span></span>  
  
|<span data-ttu-id="18a00-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="18a00-109">Attribute</span></span>|<span data-ttu-id="18a00-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="18a00-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18a00-111">codificado</span><span class="sxs-lookup"><span data-stu-id="18a00-111">encodedValue</span></span>|<span data-ttu-id="18a00-112">Uma codificação base64 do certificado.</span><span class="sxs-lookup"><span data-stu-id="18a00-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18a00-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="18a00-113">Child Elements</span></span>  

 <span data-ttu-id="18a00-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="18a00-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18a00-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="18a00-115">Parent Elements</span></span>  
  
|<span data-ttu-id="18a00-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="18a00-116">Element</span></span>|<span data-ttu-id="18a00-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="18a00-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="18a00-118">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="18a00-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="18a00-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18a00-119">Example</span></span>  

 <span data-ttu-id="18a00-120">O código a seguir especifica a representação codificada de um certificado usado para validar um servidor para um cliente.</span><span class="sxs-lookup"><span data-stu-id="18a00-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="18a00-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="18a00-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="18a00-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="18a00-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
