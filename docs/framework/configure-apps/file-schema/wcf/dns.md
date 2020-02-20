---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452221"
---
# <a name="dns"></a><span data-ttu-id="54eb2-101">\<> DNS</span><span class="sxs-lookup"><span data-stu-id="54eb2-101">\<dns></span></span>
<span data-ttu-id="54eb2-102">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="54eb2-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="54eb2-103">Essa identidade é válida para o modo de autenticação de certificado X509 se o certificado do servidor contiver um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="54eb2-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="54eb2-104">Ele também é válido para o modo de autenticação do Windows se o SPN tiver o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="54eb2-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="54eb2-105">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="54eb2-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="54eb2-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="54eb2-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54eb2-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="54eb2-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="54eb2-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cliente**](client.md) ></span><span class="sxs-lookup"><span data-stu-id="54eb2-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="54eb2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ponto de extremidade**](endpoint-of-client.md) ></span><span class="sxs-lookup"><span data-stu-id="54eb2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="54eb2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Identity**](identity.md) ></span><span class="sxs-lookup"><span data-stu-id="54eb2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="54eb2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dns >**</span><span class="sxs-lookup"><span data-stu-id="54eb2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54eb2-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54eb2-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54eb2-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54eb2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="54eb2-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54eb2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54eb2-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="54eb2-115">Attributes</span></span>  
  
|<span data-ttu-id="54eb2-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="54eb2-116">Attribute</span></span>|<span data-ttu-id="54eb2-117">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="54eb2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54eb2-118">value</span><span class="sxs-lookup"><span data-stu-id="54eb2-118">value</span></span>|<span data-ttu-id="54eb2-119">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="54eb2-119">The DNS of the certificate.</span></span> <span data-ttu-id="54eb2-120">O DNS é um protocolo padrão do setor usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="54eb2-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="54eb2-121">Os usuários podem lembrar nomes de exibição, como `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165`, mais fáceis do que endereços baseados em número, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="54eb2-121">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54eb2-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54eb2-122">Child Elements</span></span>  
 <span data-ttu-id="54eb2-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="54eb2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54eb2-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54eb2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="54eb2-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="54eb2-125">Element</span></span>|<span data-ttu-id="54eb2-126">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="54eb2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54eb2-127">identidade de \<></span><span class="sxs-lookup"><span data-stu-id="54eb2-127">\<identity></span></span>](identity.md)|<span data-ttu-id="54eb2-128">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="54eb2-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54eb2-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54eb2-129">Example</span></span>  
 <span data-ttu-id="54eb2-130">O código de configuração a seguir especifica o DNS de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="54eb2-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="54eb2-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="54eb2-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="54eb2-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="54eb2-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="54eb2-133">identidade de \<></span><span class="sxs-lookup"><span data-stu-id="54eb2-133">\<identity></span></span>](identity.md)
