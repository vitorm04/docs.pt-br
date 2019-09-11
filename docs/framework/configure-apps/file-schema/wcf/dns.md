---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: c68cabd03eca71b41a0d0acce26897fa2653f4d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855365"
---
# <a name="dns"></a><span data-ttu-id="5364f-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="5364f-101">\<dns></span></span>
<span data-ttu-id="5364f-102">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="5364f-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="5364f-103">Essa identidade é válida para o modo de autenticação de certificado X509 se o certificado do servidor contiver um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="5364f-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="5364f-104">Ele também é válido para o modo de autenticação do Windows se o SPN tiver o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="5364f-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="5364f-105">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5364f-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="5364f-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5364f-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5364f-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5364f-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5364f-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="5364f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="5364f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="5364f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="5364f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="5364f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="5364f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DNS**</span><span class="sxs-lookup"><span data-stu-id="5364f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5364f-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5364f-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5364f-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5364f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5364f-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5364f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5364f-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5364f-115">Attributes</span></span>  
  
|<span data-ttu-id="5364f-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5364f-116">Attribute</span></span>|<span data-ttu-id="5364f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5364f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5364f-118">value</span><span class="sxs-lookup"><span data-stu-id="5364f-118">value</span></span>|<span data-ttu-id="5364f-119">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="5364f-119">The DNS of the certificate.</span></span> <span data-ttu-id="5364f-120">O DNS é um protocolo padrão do setor usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="5364f-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="5364f-121">Os usuários podem lembrar nomes de exibição, <https://go.microsoft.com/fwlink/?prd=10929> como [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)ou, mais fáceis do que endereços baseados em número, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="5364f-121">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5364f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5364f-122">Child Elements</span></span>  
 <span data-ttu-id="5364f-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5364f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5364f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5364f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5364f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="5364f-125">Element</span></span>|<span data-ttu-id="5364f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="5364f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5364f-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="5364f-127">\<identity></span></span>](identity.md)|<span data-ttu-id="5364f-128">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="5364f-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5364f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5364f-129">Example</span></span>  
 <span data-ttu-id="5364f-130">O código de configuração a seguir especifica o DNS de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="5364f-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="5364f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5364f-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="5364f-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5364f-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5364f-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="5364f-133">\<identity></span></span>](identity.md)
