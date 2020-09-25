---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 353d3e2d88e3515e54deadab85c37ce3be26ef29
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203859"
---
# \<userPrincipalName>

<span data-ttu-id="a5e20-101">Especifica o nome principal do usuário (UPN) de um serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a5e20-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="a5e20-102">Para obter mais informações sobre como definir o UPN, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a5e20-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="a5e20-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5e20-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5e20-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5e20-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a5e20-105">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5e20-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5e20-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5e20-106">Attributes</span></span>  
  
|<span data-ttu-id="a5e20-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="a5e20-107">Attribute</span></span>|<span data-ttu-id="a5e20-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5e20-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5e20-109">value</span><span class="sxs-lookup"><span data-stu-id="a5e20-109">value</span></span>|<span data-ttu-id="a5e20-110">Um nome de conta de usuário (às vezes chamado de nome de logon do usuário) e um nome de domínio que identifica o domínio no qual a conta de usuário está localizada.</span><span class="sxs-lookup"><span data-stu-id="a5e20-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="a5e20-111">Esse é o uso padrão para fazer logon em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5e20-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="a5e20-112">O formato é: someone@example.com (como para um endereço de email).</span><span class="sxs-lookup"><span data-stu-id="a5e20-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5e20-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5e20-113">Child Elements</span></span>  

 <span data-ttu-id="a5e20-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a5e20-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5e20-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5e20-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a5e20-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5e20-116">Element</span></span>|<span data-ttu-id="a5e20-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5e20-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="a5e20-118">Especifica a identidade do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a5e20-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e20-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5e20-119">Remarks</span></span>  

 <span data-ttu-id="a5e20-120">Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade usa o UPN ao executar a autenticação SSPI com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a5e20-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5e20-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5e20-121">Example</span></span>  

 <span data-ttu-id="a5e20-122">O código de configuração a seguir especifica o UPN do serviço a ser autenticado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="a5e20-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="a5e20-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5e20-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="a5e20-124">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="a5e20-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
