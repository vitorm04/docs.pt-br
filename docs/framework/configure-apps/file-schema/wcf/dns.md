---
title: '&lt;DNS&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 10fe4c63b08459914a16b2c736c1a454c6914a0b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145296"
---
# <a name="ltdnsgt"></a><span data-ttu-id="5e0d8-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="5e0d8-102">&lt;dns&gt;</span></span>
<span data-ttu-id="5e0d8-103">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="5e0d8-104">Essa identidade é válida para X509 modo de autenticação de certificado se o certificado do servidor contém um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="5e0d8-105">Também é válido para o modo de autenticação do Windows se o SPN tem o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="5e0d8-106">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5e0d8-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="5e0d8-107">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="5e0d8-107">\<identity></span></span>  
<span data-ttu-id="5e0d8-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="5e0d8-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0d8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e0d8-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e0d8-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e0d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e0d8-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e0d8-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e0d8-112">Attributes</span></span>  
  
|<span data-ttu-id="5e0d8-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e0d8-113">Attribute</span></span>|<span data-ttu-id="5e0d8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e0d8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e0d8-115">Valor </span><span class="sxs-lookup"><span data-stu-id="5e0d8-115">value</span></span>|<span data-ttu-id="5e0d8-116">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-116">The DNS of the certificate.</span></span> <span data-ttu-id="5e0d8-117">O DNS é um protocolo padrão da indústria usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="5e0d8-118">Os usuários conseguem lembrar como nomes de exibição [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) ou [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), mais fácil do que com base no número de endereços, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e0d8-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e0d8-119">Child Elements</span></span>  
 <span data-ttu-id="5e0d8-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e0d8-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e0d8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5e0d8-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e0d8-122">Element</span></span>|<span data-ttu-id="5e0d8-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e0d8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e0d8-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="5e0d8-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5e0d8-125">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e0d8-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e0d8-126">Example</span></span>  
 <span data-ttu-id="5e0d8-127">O código de configuração a seguir especifica que o DNS de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="5e0d8-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="5e0d8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e0d8-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="5e0d8-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="5e0d8-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5e0d8-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="5e0d8-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
