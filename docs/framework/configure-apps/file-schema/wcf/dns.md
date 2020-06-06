---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452221"
---
# \<dns>
<span data-ttu-id="df051-101">Especifica a identidade esperada do servidor.</span><span class="sxs-lookup"><span data-stu-id="df051-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="df051-102">Essa identidade é válida para o modo de autenticação de certificado X509 se o certificado do servidor contiver um DNS com o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="df051-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="df051-103">Ele também é válido para o modo de autenticação do Windows se o SPN tiver o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="df051-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="df051-104">Para obter mais informações sobre como definir o valor do elemento, consulte [identidade e autenticação de serviço](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="df051-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="df051-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df051-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df051-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df051-106">Attributes and Elements</span></span>  
 <span data-ttu-id="df051-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df051-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df051-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="df051-108">Attributes</span></span>  
  
|<span data-ttu-id="df051-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="df051-109">Attribute</span></span>|<span data-ttu-id="df051-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="df051-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df051-111">value</span><span class="sxs-lookup"><span data-stu-id="df051-111">value</span></span>|<span data-ttu-id="df051-112">O DNS do certificado.</span><span class="sxs-lookup"><span data-stu-id="df051-112">The DNS of the certificate.</span></span> <span data-ttu-id="df051-113">O DNS é um protocolo padrão do setor usado para localizar computadores em uma rede baseada em IP.</span><span class="sxs-lookup"><span data-stu-id="df051-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="df051-114">Os usuários podem lembrar nomes de exibição, como `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165` , mais fáceis do que endereços baseados em número, como 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="df051-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df051-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df051-115">Child Elements</span></span>  
 <span data-ttu-id="df051-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df051-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df051-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df051-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df051-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="df051-118">Element</span></span>|<span data-ttu-id="df051-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="df051-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="df051-120">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="df051-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df051-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df051-121">Example</span></span>  
 <span data-ttu-id="df051-122">O código de configuração a seguir especifica o DNS de um certificado X. 509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="df051-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="df051-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="df051-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="df051-124">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="df051-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
