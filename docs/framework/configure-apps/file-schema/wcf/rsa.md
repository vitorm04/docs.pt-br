---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670646"
---
# <a name="rsa"></a><span data-ttu-id="d1234-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="d1234-101">\<rsa></span></span>
<span data-ttu-id="d1234-102">Um cliente WCF seguro que se conecta a um ponto de extremidade com esta identidade verifica que as declarações apresentadas pelo servidor contém uma afirmação que contém a chave pública RSA usada para construir essa identidade.</span><span class="sxs-lookup"><span data-stu-id="d1234-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="d1234-103">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1234-103">\<identity></span></span>  
<span data-ttu-id="d1234-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="d1234-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1234-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1234-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1234-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d1234-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d1234-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1234-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1234-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1234-108">Attributes</span></span>  
  
|<span data-ttu-id="d1234-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="d1234-109">Attribute</span></span>|<span data-ttu-id="d1234-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1234-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1234-111">Valor </span><span class="sxs-lookup"><span data-stu-id="d1234-111">value</span></span>|<span data-ttu-id="d1234-112">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d1234-112">Optional String.</span></span> <span data-ttu-id="d1234-113">O RSA valor da chave pública a ser comparado com o cliente.</span><span class="sxs-lookup"><span data-stu-id="d1234-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1234-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d1234-114">Child Elements</span></span>  
 <span data-ttu-id="d1234-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d1234-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1234-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1234-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d1234-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1234-117">Element</span></span>|<span data-ttu-id="d1234-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1234-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1234-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1234-119">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d1234-120">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="d1234-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1234-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1234-121">Remarks</span></span>  
 <span data-ttu-id="d1234-122">Uma verificação RSA permite que você restrinja especificamente a autenticação para um único certificado com base em sua chave RSA ou gerado seu próprio valor de chave RSA.</span><span class="sxs-lookup"><span data-stu-id="d1234-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="d1234-123">Este permite mais rígida a autenticação de uma chave RSA específica à custa o serviço não é mais trabalhar com os clientes existentes se o valor da chave RSA é alterado.</span><span class="sxs-lookup"><span data-stu-id="d1234-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="d1234-124">Para obter mais informações sobre como usar a identidade para validar um serviço para um cliente, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d1234-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1234-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1234-125">Example</span></span>  
 <span data-ttu-id="d1234-126">O código de configuração a seguir especifica o valor de chave pública de um certificado X.509 que é usado para autenticar um servidor.</span><span class="sxs-lookup"><span data-stu-id="d1234-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="d1234-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1234-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="d1234-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d1234-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d1234-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1234-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
