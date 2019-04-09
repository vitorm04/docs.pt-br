---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188240"
---
# <a name="userprincipalname"></a><span data-ttu-id="fbd4d-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="fbd4d-101">\<userPrincipalName></span></span>
<span data-ttu-id="fbd4d-102">Especifica o usuário nome Principal (UPN) de um serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="fbd4d-103">Para obter mais informações sobre como definir o UPN, consulte [identidade de serviço e autenticação](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fbd4d-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="fbd4d-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="fbd4d-104">\<identity></span></span>  
<span data-ttu-id="fbd4d-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="fbd4d-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd4d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbd4d-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbd4d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fbd4d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fbd4d-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbd4d-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbd4d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="fbd4d-109">Attributes</span></span>  
  
|<span data-ttu-id="fbd4d-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="fbd4d-110">Attribute</span></span>|<span data-ttu-id="fbd4d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbd4d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbd4d-112">Valor </span><span class="sxs-lookup"><span data-stu-id="fbd4d-112">value</span></span>|<span data-ttu-id="fbd4d-113">Um nome de conta de usuário (também conhecido como o nome de logon do usuário) e um nome de domínio identificando o domínio no qual a conta de usuário está localizada.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="fbd4d-114">Este é o uso padrão para fazer logon em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="fbd4d-115">O formato é: someone@example.com (como um endereço de email).</span><span class="sxs-lookup"><span data-stu-id="fbd4d-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbd4d-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fbd4d-116">Child Elements</span></span>  
 <span data-ttu-id="fbd4d-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbd4d-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbd4d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fbd4d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbd4d-119">Element</span></span>|<span data-ttu-id="fbd4d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbd4d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbd4d-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="fbd4d-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="fbd4d-122">Especifica a identidade do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbd4d-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbd4d-123">Remarks</span></span>  
 <span data-ttu-id="fbd4d-124">Um cliente seguro do Windows Communication Foundation (WCF) que se conecta a um ponto de extremidade com esta identidade usa o UPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbd4d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbd4d-125">Example</span></span>  
 <span data-ttu-id="fbd4d-126">O código de configuração a seguir especifica o UPN do serviço para ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="fbd4d-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="fbd4d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbd4d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="fbd4d-128">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="fbd4d-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fbd4d-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="fbd4d-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
