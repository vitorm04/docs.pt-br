---
title: '&lt;DNS&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 6125bf157d04a1b0298a183465d11a18ac3786f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746729"
---
# <a name="ltdnsgt"></a><span data-ttu-id="f192e-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="f192e-102">&lt;dns&gt;</span></span>
<span data-ttu-id="f192e-103">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="f192e-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="f192e-104">Essa identidade é válida para X509 modo de autenticação de certificado, se o certificado do servidor contém um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="f192e-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="f192e-105">Também é válido para o modo de autenticação do Windows se o SPN tem o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="f192e-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="f192e-106">Para obter mais informações sobre como definir o valor do elemento, consulte [autenticação e identidade de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f192e-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="f192e-107">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="f192e-107">\<identity></span></span>  
<span data-ttu-id="f192e-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="f192e-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f192e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f192e-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f192e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f192e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f192e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f192e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f192e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f192e-112">Attributes</span></span>  
  
|<span data-ttu-id="f192e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f192e-113">Attribute</span></span>|<span data-ttu-id="f192e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f192e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f192e-115">Valor </span><span class="sxs-lookup"><span data-stu-id="f192e-115">value</span></span>|<span data-ttu-id="f192e-116">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="f192e-116">The DNS of the certificate.</span></span> <span data-ttu-id="f192e-117">O DNS é um protocolo padrão da indústria usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="f192e-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="f192e-118">Os usuários conseguem lembrar nomes para exibição, como [ http://go.microsoft.com/fwlink/?prd=10929 ](http://go.microsoft.com/fwlink/?prd=10929) ou [ http://go.microsoft.com/fwlink/?LinkID=96165 ](http://go.microsoft.com/fwlink/?LinkID=96165), mais fácil do que endereços baseados em número, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="f192e-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f192e-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f192e-119">Child Elements</span></span>  
 <span data-ttu-id="f192e-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f192e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f192e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f192e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f192e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f192e-122">Element</span></span>|<span data-ttu-id="f192e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f192e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f192e-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="f192e-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="f192e-125">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="f192e-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f192e-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f192e-126">Example</span></span>  
 <span data-ttu-id="f192e-127">O código de configuração a seguir especifica o DNS de um certificado x. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="f192e-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f192e-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f192e-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="f192e-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="f192e-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f192e-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="f192e-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
