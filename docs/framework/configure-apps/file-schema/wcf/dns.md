---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: ce12d0a82c8a443994559ed772496897f359b4e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166667"
---
# <a name="dns"></a><span data-ttu-id="c92da-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="c92da-101">\<dns></span></span>
<span data-ttu-id="c92da-102">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="c92da-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="c92da-103">Essa identidade é válida para X509 modo de autenticação de certificado se o certificado do servidor contém um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="c92da-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="c92da-104">Também é válido para o modo de autenticação do Windows se o SPN tem o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="c92da-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="c92da-105">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c92da-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="c92da-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="c92da-106">\<identity></span></span>  
<span data-ttu-id="c92da-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="c92da-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92da-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c92da-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c92da-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c92da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c92da-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c92da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c92da-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c92da-111">Attributes</span></span>  
  
|<span data-ttu-id="c92da-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c92da-112">Attribute</span></span>|<span data-ttu-id="c92da-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c92da-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c92da-114">Valor </span><span class="sxs-lookup"><span data-stu-id="c92da-114">value</span></span>|<span data-ttu-id="c92da-115">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="c92da-115">The DNS of the certificate.</span></span> <span data-ttu-id="c92da-116">O DNS é um protocolo padrão da indústria usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="c92da-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="c92da-117">Os usuários conseguem lembrar como nomes de exibição [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) ou [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), mais fácil do que com base no número de endereços, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="c92da-117">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c92da-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c92da-118">Child Elements</span></span>  
 <span data-ttu-id="c92da-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c92da-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c92da-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c92da-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c92da-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c92da-121">Element</span></span>|<span data-ttu-id="c92da-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c92da-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c92da-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="c92da-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c92da-124">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c92da-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c92da-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c92da-125">Example</span></span>  
 <span data-ttu-id="c92da-126">O código de configuração a seguir especifica que o DNS de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="c92da-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c92da-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c92da-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="c92da-128">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="c92da-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c92da-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="c92da-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
