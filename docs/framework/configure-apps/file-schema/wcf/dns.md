---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919130"
---
# <a name="dns"></a><span data-ttu-id="cac68-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="cac68-101">\<dns></span></span>
<span data-ttu-id="cac68-102">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="cac68-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="cac68-103">Essa identidade é válida para o modo de autenticação de certificado X509 se o certificado do servidor contiver um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="cac68-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="cac68-104">Ele também é válido para o modo de autenticação do Windows se o SPN tiver o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="cac68-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="cac68-105">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cac68-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="cac68-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="cac68-106">\<identity></span></span>  
<span data-ttu-id="cac68-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="cac68-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac68-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cac68-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cac68-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cac68-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cac68-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cac68-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cac68-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="cac68-111">Attributes</span></span>  
  
|<span data-ttu-id="cac68-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="cac68-112">Attribute</span></span>|<span data-ttu-id="cac68-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cac68-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cac68-114">value</span><span class="sxs-lookup"><span data-stu-id="cac68-114">value</span></span>|<span data-ttu-id="cac68-115">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="cac68-115">The DNS of the certificate.</span></span> <span data-ttu-id="cac68-116">O DNS é um protocolo padrão do setor usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="cac68-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="cac68-117">Os usuários podem lembrar nomes de exibição, <https://go.microsoft.com/fwlink/?prd=10929> como [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)ou, mais fáceis do que endereços baseados em número, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="cac68-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cac68-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cac68-118">Child Elements</span></span>  
 <span data-ttu-id="cac68-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cac68-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cac68-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cac68-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cac68-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="cac68-121">Element</span></span>|<span data-ttu-id="cac68-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="cac68-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cac68-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="cac68-123">\<identity></span></span>](identity.md)|<span data-ttu-id="cac68-124">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="cac68-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cac68-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cac68-125">Example</span></span>  
 <span data-ttu-id="cac68-126">O código de configuração a seguir especifica o DNS de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="cac68-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="cac68-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cac68-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="cac68-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="cac68-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cac68-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="cac68-129">\<identity></span></span>](identity.md)
