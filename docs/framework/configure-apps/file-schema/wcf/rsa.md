---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855050"
---
# <a name="rsa"></a><span data-ttu-id="a46e6-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="a46e6-101">\<rsa></span></span>
<span data-ttu-id="a46e6-102">Um cliente WCF seguro que se conecta a um ponto de extremidade com essa identidade verifica se as declarações apresentadas pelo servidor contêm uma declaração que contém a chave pública RSA usada para construir essa identidade.</span><span class="sxs-lookup"><span data-stu-id="a46e6-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
<span data-ttu-id="a46e6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a46e6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a46e6-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a46e6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a46e6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="a46e6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="a46e6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="a46e6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="a46e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="a46e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="a46e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**</span><span class="sxs-lookup"><span data-stu-id="a46e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a46e6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a46e6-109">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a46e6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a46e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a46e6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a46e6-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a46e6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a46e6-112">Attributes</span></span>  
  
|<span data-ttu-id="a46e6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a46e6-113">Attribute</span></span>|<span data-ttu-id="a46e6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46e6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a46e6-115">value</span><span class="sxs-lookup"><span data-stu-id="a46e6-115">value</span></span>|<span data-ttu-id="a46e6-116">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="a46e6-116">Optional String.</span></span> <span data-ttu-id="a46e6-117">O valor da chave pública RSA a ser comparado no cliente.</span><span class="sxs-lookup"><span data-stu-id="a46e6-117">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a46e6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a46e6-118">Child Elements</span></span>  
 <span data-ttu-id="a46e6-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a46e6-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a46e6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a46e6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a46e6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a46e6-121">Element</span></span>|<span data-ttu-id="a46e6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46e6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a46e6-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="a46e6-123">\<identity></span></span>](identity.md)|<span data-ttu-id="a46e6-124">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a46e6-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a46e6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a46e6-125">Remarks</span></span>  
 <span data-ttu-id="a46e6-126">Uma verificação RSA permite restringir especificamente a autenticação a um único certificado com base em sua chave RSA ou gerar seu próprio valor de chave RSA.</span><span class="sxs-lookup"><span data-stu-id="a46e6-126">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="a46e6-127">Isso permite a autenticação mais estrita de uma chave RSA específica na despesa do serviço que não está mais funcionando com os clientes existentes se o valor da chave RSA for alterado.</span><span class="sxs-lookup"><span data-stu-id="a46e6-127">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="a46e6-128">Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a46e6-128">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a46e6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a46e6-129">Example</span></span>  
 <span data-ttu-id="a46e6-130">O código de configuração a seguir especifica o valor de chave pública de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="a46e6-130">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="a46e6-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a46e6-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="a46e6-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a46e6-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a46e6-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="a46e6-133">\<identity></span></span>](identity.md)
