---
title: '&lt;rsa&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 74da1e2ae02f151f928afec24d6af3adf703bdcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612772"
---
# <a name="ltrsagt"></a><span data-ttu-id="16efd-102">&lt;rsa&gt;</span><span class="sxs-lookup"><span data-stu-id="16efd-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="16efd-103">Um cliente WCF seguro que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contém uma afirmação que contém a chave pública RSA usada para construir essa identidade.</span><span class="sxs-lookup"><span data-stu-id="16efd-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="16efd-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="16efd-104">\<identity></span></span>  
<span data-ttu-id="16efd-105">\<rsa></span><span class="sxs-lookup"><span data-stu-id="16efd-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16efd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16efd-106">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16efd-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16efd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="16efd-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="16efd-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16efd-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="16efd-109">Attributes</span></span>  
  
|<span data-ttu-id="16efd-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="16efd-110">Attribute</span></span>|<span data-ttu-id="16efd-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="16efd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16efd-112">Valor </span><span class="sxs-lookup"><span data-stu-id="16efd-112">value</span></span>|<span data-ttu-id="16efd-113">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="16efd-113">Optional String.</span></span> <span data-ttu-id="16efd-114">O RSA valor da chave pública a ser comparado com o cliente.</span><span class="sxs-lookup"><span data-stu-id="16efd-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16efd-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="16efd-115">Child Elements</span></span>  
 <span data-ttu-id="16efd-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="16efd-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16efd-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="16efd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="16efd-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="16efd-118">Element</span></span>|<span data-ttu-id="16efd-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="16efd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16efd-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="16efd-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="16efd-121">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="16efd-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16efd-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="16efd-122">Remarks</span></span>  
 <span data-ttu-id="16efd-123">Uma verificação RSA permite que você restrinja especificamente a autenticação para um único certificado com base em sua chave RSA ou gerado seu próprio valor de chave RSA.</span><span class="sxs-lookup"><span data-stu-id="16efd-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="16efd-124">Este permite mais rígida a autenticação de uma chave RSA específica à custa o serviço não é mais trabalhar com os clientes existentes se o valor da chave RSA é alterado.</span><span class="sxs-lookup"><span data-stu-id="16efd-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="16efd-125">Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="16efd-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16efd-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16efd-126">Example</span></span>  
 <span data-ttu-id="16efd-127">O código de configuração a seguir especifica o valor de chave pública de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="16efd-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="16efd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16efd-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="16efd-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="16efd-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="16efd-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="16efd-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
