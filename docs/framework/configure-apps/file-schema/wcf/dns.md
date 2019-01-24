---
title: '&lt;dns&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 68cbb25b79bbda301c29d72800a125c7a6ba0b6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616453"
---
# <a name="ltdnsgt"></a><span data-ttu-id="e8755-102">&lt;dns&gt;</span><span class="sxs-lookup"><span data-stu-id="e8755-102">&lt;dns&gt;</span></span>
<span data-ttu-id="e8755-103">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="e8755-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e8755-104">Essa identidade é válida para X509 modo de autenticação de certificado se o certificado do servidor contém um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="e8755-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e8755-105">Também é válido para o modo de autenticação do Windows se o SPN tem o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="e8755-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="e8755-106">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8755-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e8755-107">\<identity></span><span class="sxs-lookup"><span data-stu-id="e8755-107">\<identity></span></span>  
<span data-ttu-id="e8755-108">\<dns></span><span class="sxs-lookup"><span data-stu-id="e8755-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8755-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8755-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8755-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e8755-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e8755-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e8755-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8755-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8755-112">Attributes</span></span>  
  
|<span data-ttu-id="e8755-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e8755-113">Attribute</span></span>|<span data-ttu-id="e8755-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8755-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8755-115">Valor </span><span class="sxs-lookup"><span data-stu-id="e8755-115">value</span></span>|<span data-ttu-id="e8755-116">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="e8755-116">The DNS of the certificate.</span></span> <span data-ttu-id="e8755-117">O DNS é um protocolo padrão da indústria usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="e8755-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e8755-118">Os usuários conseguem lembrar como nomes de exibição [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) ou [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), mais fácil do que com base no número de endereços, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="e8755-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8755-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e8755-119">Child Elements</span></span>  
 <span data-ttu-id="e8755-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e8755-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8755-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e8755-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e8755-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8755-122">Element</span></span>|<span data-ttu-id="e8755-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8755-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8755-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="e8755-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e8755-125">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="e8755-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8755-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8755-126">Example</span></span>  
 <span data-ttu-id="e8755-127">O código de configuração a seguir especifica que o DNS de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="e8755-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e8755-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8755-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e8755-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e8755-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e8755-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="e8755-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
