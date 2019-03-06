---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: eb5459625cf58feeef5ba29d76e74691a4f87cc8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364691"
---
# <a name="dns"></a><span data-ttu-id="e1979-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="e1979-101">\<dns></span></span>
<span data-ttu-id="e1979-102">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="e1979-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e1979-103">Essa identidade é válida para X509 modo de autenticação de certificado se o certificado do servidor contém um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="e1979-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e1979-104">Também é válido para o modo de autenticação do Windows se o SPN tem o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="e1979-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="e1979-105">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e1979-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e1979-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="e1979-106">\<identity></span></span>  
<span data-ttu-id="e1979-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="e1979-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1979-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1979-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1979-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1979-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1979-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1979-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1979-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1979-111">Attributes</span></span>  
  
|<span data-ttu-id="e1979-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e1979-112">Attribute</span></span>|<span data-ttu-id="e1979-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1979-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1979-114">Valor </span><span class="sxs-lookup"><span data-stu-id="e1979-114">value</span></span>|<span data-ttu-id="e1979-115">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="e1979-115">The DNS of the certificate.</span></span> <span data-ttu-id="e1979-116">O DNS é um protocolo padrão da indústria usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="e1979-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e1979-117">Os usuários conseguem lembrar como nomes de exibição [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) ou [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), mais fácil do que com base no número de endereços, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="e1979-117">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1979-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1979-118">Child Elements</span></span>  
 <span data-ttu-id="e1979-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1979-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1979-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1979-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1979-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1979-121">Element</span></span>|<span data-ttu-id="e1979-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1979-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1979-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="e1979-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e1979-124">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="e1979-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1979-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1979-125">Example</span></span>  
 <span data-ttu-id="e1979-126">O código de configuração a seguir especifica que o DNS de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="e1979-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e1979-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1979-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e1979-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e1979-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e1979-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="e1979-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
